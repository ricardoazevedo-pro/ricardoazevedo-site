# ricardoazevedo.pro

Personal portfolio for [Ricardo Azevedo](https://ricardoazevedo.pro) — IT engineer and backend developer based in Portugal.

[![Live](https://img.shields.io/badge/live-ricardoazevedo.pro-3b82f6?style=flat-square&logo=firefox&logoColor=white)](https://ricardoazevedo.pro)
[![License](https://img.shields.io/badge/license-MIT-22c55e?style=flat-square)](./LICENSE)

---

## Stack

- **HTML + CSS + Vanilla JS** — zero dependencies, no build step
- Single `index.html` — self-contained, deployable anywhere
- Google Fonts (IBM Plex Sans + IBM Plex Mono) via CDN
- IntersectionObserver for scroll reveal animations
- Fully responsive

## Structure

```
ricardoazevedo.pro/
└── index.html        # everything lives here
```

## Running locally

No setup required. Open `index.html` directly in a browser, or serve it with any static file server:

```bash
# Python
python -m http.server 3000

# Node (npx)
npx serve .
```

## Deploying

Hosted on a self-managed web server running **CyberPanel**. Deployments are fully automatic via GitHub webhook.

### How it works

```
git push origin main
       │
       ▼
GitHub webhook fires (POST)
       │
       ▼
Server receives request → runs git pull
       │
       ▼
ricardoazevedo.pro updates live
```

### Webhook setup (CyberPanel)

1. On the server, make sure the site's document root is a git repo tracking `main`
2. Create a webhook script (e.g. `deploy.php` or a small Python/Node listener) that runs `git pull origin main`
3. In GitHub → Settings → Webhooks → Add webhook:
   - **Payload URL**: `https://ricardoazevedo.pro/deploy.php` (or your listener endpoint)
   - **Content type**: `application/json`
   - **Secret**: set a secret token and validate it in your script
   - **Event**: Just the `push` event → filtered to `main`
4. On merge to `main`, GitHub fires the webhook → server pulls → site is live within seconds

No CI, no build step, no pipeline. Push and it's done.

## Customising

All content is in a single file. Key sections:

| Section | What to edit |
|---|---|
| Hero | Name, role, tagline, terminal content |
| About | Bio text, sidebar info cards |
| Stack | Tag lists and `.hi` / `.learning` classes |
| Projects | Project cards — name, description, links |
| Security | Bullet points and meter fill widths |
| Contact | LinkedIn and GitHub links |

CSS variables are at the top of the `<style>` block — colours, fonts, and spacing are all centralised there.

## License

MIT — fork it, adapt it, ship it.
