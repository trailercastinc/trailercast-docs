# TrailerCast docs (Mintlify)

This directory is the source for [docs.trailercast.io](https://docs.trailercast.io). Push to the `trailercastinc/trailercast-docs` GitHub repo (public) and Mintlify auto-deploys on every commit.

## Structure

- `docs.json` — Mintlify config (navigation, branding, social links, search)
- `*.mdx` — content pages
- `setup/`, `trailers/` — grouped sub-pages
- `images/` — screenshots, OG images, logo
- `pdf-archive/` — original PDFs preserved as downloadable artifacts (linked from each page's "Download as PDF" button)

## Editing

```bash
# Install Mintlify CLI once
npm install -g mint

# Run locally with hot reload
cd docs-site
mint dev
```

Then open `http://localhost:3000`.

## Deploying

Push to the public repo's `main` branch — Mintlify auto-deploys within ~30s.

```bash
cd docs-site
git add .
git commit -m "Update docs"
git push
```

## Adding a new page

1. Create `new-page.mdx` with frontmatter:
   ```mdx
   ---
   title: "My new page"
   description: "Short description for SEO + page hover"
   icon: "rocket"
   ---

   Content here…
   ```
2. Add the page slug to `docs.json` under the appropriate group.
3. Commit + push.

## Adding to a custom domain

`docs.trailercast.io` should `CNAME` to Mintlify's hosting (instructions on Mintlify dashboard). Cloudflare DNS lives at trailercast.io's account; add the CNAME there.

## Components reference

Mintlify ships these MDX components — use freely:

- `<Card>` and `<CardGroup cols={2|3|4}>`
- `<Steps>` and `<Step title="…">`
- `<Tabs>` and `<Tab title="…">`
- `<AccordionGroup>` and `<Accordion title="…">`
- `<Note>`, `<Tip>`, `<Warning>`
- `<Frame>` for screenshots with a polished border
- `<Update label="2026-05-08" description="…">` for changelog entries

## Linking from inside the TrailerCast app

The in-app **? Help** menu (top-right, near profile) deep-links to docs pages via the slug system:

- `getting-started` → `/quickstart`
- `recording` → `/recording`
- `trailers/reviewing` → `/trailers/reviewing`
- `setup/ai-personalization` → `/setup/ai-personalization`
- etc.

The app's `phaseToHelpSlug()` in `frontend/src/App.jsx` is the source of truth for the mapping.
