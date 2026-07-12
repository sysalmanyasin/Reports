# Branch Operations Hub

Fazal Din's Pharma Plus — Manga Mandi branch tools, all in one place.

## Live site

Once hosted on GitHub Pages, open:
`https://<your-username>.github.io/<repo-name>/`

That loads `index.html`, the cover dashboard, with cards linking to each tool below.

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The cover dashboard — start here |
| `daily_report.html` | Daily Check List — sales, stock, sign-off report |
| `excess-stock-control.html` | Excess Stock Control — multi-branch inventory tracking |
| `manifest.json`, `sw.js`, `icon-*.png`, `apple-touch-icon.png` | PWA files so the hub can be installed as an app and work offline |

Everything is self-contained, single-file HTML — no server, database, or build step required. Works fully offline once loaded.

## Adding a new module

1. Save the new tool as a single HTML file in this same folder.
2. Open `index.html`, find the `MODULES` list near the bottom of the `<script>` section.
3. Add one entry, following the commented example already there:

```js
{
  name: "Tool Name",
  description: "One line describing what it does.",
  href: "./your-file-name.html",
  icon: "₨",       // any short emoji or symbol
  color: "blue",    // "green", "amber", "blue", or "teal"
  status: "Ready"
}
```

4. Save and re-upload `index.html` (and the new tool file) to GitHub.

No other changes needed — the dashboard builds its cards from this list automatically.

### Linking to a tool hosted elsewhere

Some tools — like Shift Register & Closing — are full multi-file apps deployed to their own domain instead of living in this folder. For those, use a full URL as `href` and add `external: true`:

```js
{
  name: "Shift Register & Closing",
  description: "Cash reconciliation, credit ledger, and daily/period closing reports.",
  href: "https://closing.duapharma.com",
  icon: "💊",
  color: "teal",
  status: "Ready",
  external: true
}
```

`external: true` opens the card in a new tab and shows a "Hosted ↗" tag instead of "Ready", so it's clear the tool lives outside this repo.

## Updating an existing tool

Just re-upload the changed HTML file through GitHub's **Add file → Upload files**, overwriting the old one. Pages will redeploy automatically within a minute or two.
