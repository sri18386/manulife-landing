# Manulife × Accenture × Lyzr — Landing Page

A single-file static landing page for the agentic-AI demo. It sets context (the India
life-insurance value chain + demo callout) and links natively into Shikhar's app for the
two live journeys and the organizational-intelligence view.

## Contents

```
index.html        the whole page (HTML + CSS + JS inline)
assets/
  manulife.svg    Manulife logo (Wikimedia Commons)
  accenture.svg   Accenture logo (Wikimedia Commons)
  lyzr.png        Lyzr logo
render.yaml        Render static-site blueprint
netlify.toml       Netlify config
vercel.json        Vercel config
```

No build step. No dependencies. Just static files.

## Configure the app links (do this first)

Open `index.html`, find the config block near the bottom, and set the routes to match
Shikhar's deployed app:

```js
const APP = "https://manulife-underwriting-web.onrender.com";
const ROUTES = {
  onboarding:   "/onboarding-live",   // confirmed
  underwriting: "/underwriting",      // ASSUMPTION — confirm with Shikhar
  intelligence: "/intelligence"       // ASSUMPTION — confirm with Shikhar
};
```

Each journey section loads the matching route in an inline iframe on click, with an
"Open ↗" full-screen fallback. If the app blocks iframe embedding (X-Frame-Options /
frame-ancestors), the fallback opens it in a new tab automatically.

## Preview locally

Any static server works, e.g.:

```bash
npx serve .
# or
python3 -m http.server 4599
```

Then open http://localhost:4599

## Deploy

- **Netlify** — drag this folder onto app.netlify.com/drop, or connect the repo (config in `netlify.toml`).
- **Render** — New → Static Site, point at this folder; `render.yaml` is included.
- **Vercel** — `vercel deploy` from this folder (`vercel.json` included).
- **GitHub Pages / S3 / any CDN** — upload the folder; `index.html` is the entry point.

## Design notes

Type and palette are matched to Shikhar's app so the in-page dive-ins feel native:
Playfair Display (headings), DM Sans (body), JetBrains Mono (mono); cream/beige surfaces
with Manulife green + warm gold/espresso accents. Fonts load from Google Fonts CDN.
