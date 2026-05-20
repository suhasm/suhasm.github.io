# CLAUDE.md

Personal academic website for Suhas Mahesh. Custom domain: **suhasmahesh.com** (set via `CNAME`). Live at https://suhasm.github.io.

Built on the [al-folio](https://github.com/alshedivat/al-folio) Jekyll template (forked via Toni Deleo's fork). Most of the template machinery is upstream — only the content files and `_config.yml` are customized.

## Where content lives

| Editing task | Path |
|---|---|
| About page / bio | `_pages/about.md` |
| News items (homepage feed) | `_news/announcement_*.md` |
| CV content | `_data/cv.yml` and `_pages/cv.md` |
| Publications (BibTeX) | `_bibliography/papers.bib` |
| Projects | `_projects/*.md` |
| Blog posts | `_posts/YYYY-MM-DD-*.md` |
| Profile photo, PDFs, images | `assets/` |
| Site config (title, socials, nav, theme) | `_config.yml` |

## Where NOT to edit

- `INSTALL.md`, `CUSTOMIZE.md`, `FAQ.md`, `CONTRIBUTING.md` — upstream template docs, not Suhas's writing
- `_pages/about_einstein.md` — upstream demo page
- `_posts/2015-*` through `_posts/2024-*` (the dated template demos) — these are al-folio demo posts showing markdown features, not Suhas's blog. The site currently has no real blog posts.
- `_layouts/`, `_includes/`, `_sass/`, `_plugins/` — template internals. Edit only when changing site behavior, not content.
- `readme_preview/`, `lighthouse_results/` — auto-generated

## Local development

```bash
bundle exec jekyll serve   # http://localhost:4000
```
Or use Docker: `docker compose up`. The `bin/entry_point.sh` script handles `_config.yml` live-reload inside the container.

## Deploy

GitHub Actions (`.github/workflows/deploy.yml`) builds on push to `master` and publishes to `gh-pages`. Triggers on changes to content, assets, configs — explicitly skips template docs (`INSTALL.md` etc.).

Don't push directly to `gh-pages`; that branch is overwritten by the workflow.

## News item format

Inline announcements (no separate page). Date-ordered by filename — `announcement_8.md` is the newest. Frontmatter pattern:

```yaml
---
layout: post
date: 2025-MM-DD HH:MM:00-0400
inline: true
related_posts: false
---
Short markdown text with [links](url).
```

## Publication format

Add to `_bibliography/papers.bib` as standard BibTeX. The `selected={true}` field promotes a paper to the highlighted list. `preview={filename.png}` adds a thumbnail from `assets/img/publication_preview/`.

## Conventions for this site

- Suhas does not use a blog. Don't add new posts to `_posts/` unless he asks.
- News items are short, factual, often link to an external post (X, paper, talk). One sentence is fine.
- The `about.md` page is the site's center of gravity — most edits to "who I am" go there, not into `_config.yml`.
- Commit messages on this repo are terse and lowercase ("updated about me", "added PNAS paper on arxiv news"). Match that style.
