# NoDwell Pitch Deck Gallery

Central hub for all NoDwell pitch decks — personalized investor presentations, general decks, and branch variants. Every deck is live on Netlify with custom domains on `getnodwell.com`.

---

## What This Is

This is a single-page hub that links to **all 22 NoDwell pitch decks** deployed across Netlify. Each deck is a standalone HTML presentation (built with Reveal.js or custom HTML/CSS) hosted in its own GitHub repo and deployed via Netlify. Some have custom domains on `getnodwell.com` via GoDaddy CNAME records.

The hub provides:
- **Filterable card grid** — filter by Personalized, General, Branch Variant, or Other
- **Live status indicators** — green dot shows active deployment
- **Direct links** to every deck, with repo links to source code
- **Custom domain badges** — shows which decks have `*.getnodwell.com` domains vs Netlify subdomains
- **Dark mode, glassmorphism UI** — polished look that matches the NoDwell brand

---

## Project Structure

```
nodwell-deck-gallery/
├── index.html          # The entire hub — single file, no build step
└── README.md           # This file
```

This is a **zero-dependency, zero-build** static site. Just an `index.html` file. No npm, no framework, no build tools. It uses:
- **Inter** font from Google Fonts
- **Vanilla CSS** with CSS custom properties for the design system
- **Vanilla JavaScript** for filtering and card rendering

---

## Deck Inventory (22 Decks)

### Personalized Decks (7)
| Deck | Domain | Repo |
|------|--------|------|
| CampX (Volvo) | `campx.getnodwell.com` | `rblappan/campxdeck_detailed` |
| Cargill | `cargill.getnodwell.com` | `rblappan/cargilldeck_detailed` |
| Invest Midwest | `investmidwest.getnodwell.com` | `rblappan/invest_midwest_deck` |
| proChain Ventures | `prochain.getnodwell.com` | `rblappan/prochainventuresdeck_detailed` |
| Sope Creek (Series A - Full) | `nodwell-sopecreek-capital.netlify.app` | `rblappan/nodwell-pitch-sopecreek` |
| Sope Creek Pre-Seed | `nodwell-sopecreek-preseed.netlify.app` | `rblappan/sopecreekpreseed_detailed_personalized` |
| Supply Chain Ventures | `supplychainventures.getnodwell.com` | `rblappan/supplychainventuresdeck_detailed` |

### General Decks (4)
| Deck | Domain | Repo |
|------|--------|------|
| FINAL General Deck ($54M) | `deckseriesafinal10.getnodwell.com` | `rblappan/FINALgeneraldeck` |
| ND Last 10% Raise | `seriesainvestorportal.getnodwell.com` | `rblappan/NDlast10-raise` |
| NoDwell Deck Beta | `nodwell-deck-beta.netlify.app` | `rblappan/nodwell_deck_beta` |
| General Deck (Detailed) | `preseeddeck.getnodwell.com` | `rblappan/nodwellgeneraldeck_detailed` |

### Branch Variants (7)
| Deck | Branch | Domain | Repo |
|------|--------|--------|------|
| FINAL General ($6M) | `6m-raise` | `nodwell-6m-raise-deck.netlify.app` | `rblappan/FINALgeneraldeck` |
| ND Last 10% (Bridge) | `bridge` | `nodwell-nd10-bridge.netlify.app` | `rblappan/NDlast10-raise` |
| ND Last 10% (Pre-Seed/Series A) | `preseed-series-a` | `nodwell-nd10-preseed-seriesa.netlify.app` | `rblappan/NDlast10-raise` |
| General Deck (Series A Bridged) | `seriesabridgedeck` | `seriesabridgedeck.getnodwell.com` | `rblappan/nodwellgeneraldeck_detailed` |
| Sope Creek (General Branch) | `generaldeck_detailed` | `nodwell-sopecreek-general.netlify.app` | `rblappan/sopecreekpreseed_detailed_personalized` |
| Sope Creek (Series A Personalized) | `series-a-personalized` | `nodwell-sopecreek-seriesa.netlify.app` | `rblappan/sopecreekpreseed_detailed_personalized` |
| Sope Creek (Series A Bridged) | `seriesabridgedeck` | `nodwell-sopecreek-abridged.netlify.app` | `rblappan/sopecreekpreseed_detailed_personalized` |

### Other Presentations (4)
| Deck | Domain | Repo |
|------|--------|------|
| Hardware Strategy | `nodwell-hardware-strategy.netlify.app` | `rblappan/HardwareStradegy` |
| Ballast AI Presentation | `nodwell-ai-presentation.netlify.app` | `rblappan/aipresentation` |
| NoDwell vs Baton Comparison | `nodwell-baton-comparison.netlify.app` | `rblappan/nodwellbatoncomparrison` |
| Personal Tesla Plan | `nodwell-personal-tesla.netlify.app` | `rblappan/personalteslaplan` |

---

## How to Run Locally

```bash
# Option 1: Python
python3 -m http.server 8000

# Option 2: Node (npx)
npx serve .

# Option 3: Just open the file
open index.html
```

Then visit `http://127.0.0.1:8000` (or whatever port your server uses).

---

## How to Deploy to Netlify

1. Connect this repo to Netlify
2. Build command: (leave blank — no build step)
3. Publish directory: `.` (root)
4. Deploy

Or just drag the folder into Netlify's deploy drop zone.

---

## How to Add a New Deck

Edit `index.html` and add an object to the `decks` array in the `<script>` section (around line 343):

```javascript
{
  name: "New Deck Name",
  desc: "Short description of this deck",
  url: "https://your-deck-url.netlify.app",
  domain: "your-deck-url.netlify.app",
  customDomain: false,  // true if using *.getnodwell.com
  branch: "main",       // or the branch name
  category: "personalized",  // personalized | general | branch | other
  repo: "rblappan/repo-name"
}
```

---

## Custom Domain Setup (for `*.getnodwell.com`)

When a deck gets a custom domain:
1. Go to **GoDaddy** → DNS → Add CNAME record
2. Name: subdomain (e.g., `campx`)
3. Value: the Netlify app URL (e.g., `campxdeck-detailed.netlify.app`)
4. Go to **Netlify** → Domain Settings → Add custom domain
5. Wait for SSL to provision (usually < 5 min)
6. Update the deck entry in this hub's `index.html`

---

## Design System

The hub uses a dark theme with these CSS custom properties:

| Token | Value | Use |
|-------|-------|-----|
| `--bg` | `#0a0a0f` | Page background |
| `--surface` | `#12121a` | Card backgrounds |
| `--accent` | `#8b5cf6` | Purple accent (primary) |
| `--green` | `#22c55e` | Success, live indicators |
| `--cyan` | `#06b6d4` | Secondary accent |
| `--amber` | `#f59e0b` | Branch tags, warnings |
| `--text` | `#e2e2ef` | Primary text |
| `--text-muted` | `#8888a0` | Secondary text |

Font: **Inter** (300–800 weights) via Google Fonts.

---

## AI Agent Prompt (for Antigravity / Cursor / etc.)

If you're using an AI coding agent and want it to understand this project on first load, paste this into your system prompt or first message:

---

> **Context for AI Agent:**
>
> This repo (`nodwell-deck-gallery`) is a **single-page static hub** that links to 22+ NoDwell pitch decks hosted on Netlify. The entire app is one `index.html` file — no build step, no dependencies, no framework.
>
> **Architecture:**
> - All deck data is in a JavaScript `decks` array inside `<script>` tags at the bottom of `index.html` (starts around line 343)
> - Each deck object has: `name`, `desc`, `url`, `domain`, `customDomain` (bool), `branch`, `category`, `repo`
> - Categories are: `personalized`, `general`, `branch`, `other`
> - Filtering is done client-side via `renderCards(filter)` function
> - Cards are `<a>` elements that open in new tabs
>
> **Design:**
> - Dark theme using CSS custom properties in `:root`
> - Uses Inter font from Google Fonts
> - Cards have hover effects with `translateY(-4px)` and purple glow
> - Animated gradient top bar on hover
> - Filter tabs use `.active` class toggle
> - Cards have staggered `fadeSlideIn` animation on render
>
> **Business context:**
> - NoDwell is a freight technology startup that eliminates dwell time (trucks waiting at docks)
> - "Personalized" decks are tailored to specific investors/partners (CampX/Volvo, Cargill, proChain Ventures, etc.)
> - "General" decks are the standard pitch decks for broad use
> - "Branch variants" are alternate versions of the same deck repo deployed from different git branches (e.g., `6m-raise`, `bridge`, `preseed-series-a`, `seriesabridgedeck`)
> - Custom domains are on `*.getnodwell.com` managed via GoDaddy CNAME records
> - All decks are deployed via Netlify, connected to GitHub repos under `rblappan/*`
>
> **Common tasks:**
> - Adding a new deck: Add an object to the `decks` array
> - Changing a deck URL: Update the `url` and `domain` fields
> - Changing categories: Update the `category` field
> - Styling changes: Edit CSS custom properties in `:root` or the card styles
> - The hub itself can be deployed to Netlify (no build command needed, publish dir is `.`)
>
> **Related repos** (all under `rblappan/`):
> - Each deck has its own repo listed in the `repo` field
> - The canonical "base deck" for personalization is `prochainventuresdeck_detailed`
> - Branch deploys use Netlify's branch deploy feature
>
> **Known quirks:**
> - Two repo names have typos that are intentional (they're the actual GitHub repo names): `HardwareStradegy` and `nodwellbatoncomparrison`
> - The hub currently points to Netlify URLs, not localhost — it's designed for production use
> - No favicon is included yet

---

## License

Private — NoDwell Inc. Internal use only.
