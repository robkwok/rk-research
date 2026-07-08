# Korea Leverage Monitor Static Export

Generated artifact for public static hosting.

- Entry point: `index.html`
- Data file: `korea-data.json`
- Generated at: `2026-07-08T06:00:17.779424-07:00`
- Payload fetched at: `2026-07-08T22:00:17.771248+09:00`
- Risk score: `55 / High`

This export intentionally excludes Webull positions, account data, and all trading/order code.

## Local Preview

```bash
.venv/bin/python -m http.server 8787 -d public/korea
open http://localhost:8787
```

## Rebuild

```bash
.venv/bin/python web/export_korea_site.py --out-dir public/korea
```

## Cloudflare Pages

- Build command: `python3 -m pip install -r requirements-korea.txt && python3 web/export_korea_site.py --out-dir public/korea`
- Build output directory: `public/korea`
- Deploy command if using Wrangler locally: `npx wrangler pages deploy public/korea --project-name korea-leverage-monitor`

Set these environment variables for fuller public-data history before rebuilding:

- `BOK_ECOS_API_KEY` for full BOK ECOS CD/base-rate history.
- `KOREA_FSC_SERVICE_KEY` or `DATA_GO_KR_SERVICE_KEY` for KOFIA/FSC margin, collateral, deposits, and forced-sale history.
