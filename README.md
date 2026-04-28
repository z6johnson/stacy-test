# Stacy's Boston Summer 2026

A super-lightweight static web app that helps Stacy browse events happening in Boston during summer 2026. No framework, no build step — just `index.html` + a JSON data file.

## Stack

- Static `public/index.html` (vanilla HTML/CSS/JS)
- `public/events.json` as the "backend" — Vercel serves it as a static asset with caching headers
- Deployed on Vercel as a zero-config static site

## Local development

```bash
npm run dev
```

This serves `public/` on a local port (uses `npx serve`).

Or just open `public/index.html` in a browser — `fetch("./events.json")` works from the file system in most browsers, but a local server is more reliable.

## Deploying to Vercel

1. Push this repo to GitHub.
2. Import the repo at https://vercel.com/new.
3. Vercel auto-detects this as a static project — no build command, output directory `public`.
4. Click **Deploy**.

`vercel.json` adds a small cache header to `events.json` so Vercel's edge serves it efficiently.

## Updating the events list

Edit `public/events.json` and commit. Each event has:

| field          | type    | notes                                            |
|----------------|---------|--------------------------------------------------|
| `id`           | string  | unique slug                                      |
| `name`         | string  | event name                                       |
| `category`     | string  | e.g. `music`, `festival`, `arts`, `sports`       |
| `startDate`    | string  | ISO date `YYYY-MM-DD`                            |
| `endDate`      | string  | ISO date `YYYY-MM-DD`                            |
| `neighborhood` | string  | e.g. `Back Bay`, `North End`                     |
| `venue`        | string  | location name                                    |
| `free`         | boolean | filters the "Free only" toggle                   |
| `kidFriendly`  | boolean | filters the "Kid-friendly" toggle                |
| `outdoor`      | boolean | filters the "Outdoor" toggle                     |
| `url`          | string  | optional details link                            |
| `description`  | string  | one-sentence blurb                               |

## Notes

Dates and details should be re-checked against official sources before Stacy plans her summer — these are based on each event's typical recurring schedule.
