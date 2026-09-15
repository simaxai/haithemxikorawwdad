# DEMON TEAM — Free Fire Panel

Static site. Deploys to **demonteam.vercel.app** straight from this repo.

## Repo structure (exactly this, at the root)

```
demonteam/
├── index.html      ← the whole site (pages, logic, styles)
├── vercel.json     ← security headers + deploy config
└── README.md
```

That's it. No build step, no dependencies to install — everything loads from CDNs at runtime.

## Deploy on Vercel (one time)

1. Push this folder to a GitHub repo (e.g. `simaxai/demonteam`).
2. On [vercel.com](https://vercel.com) → **Add New → Project** → import that repo.
3. Framework Preset: **Other**. Root Directory: **/** (repo root). Build Command: *(leave empty)*. Output Directory: *(leave empty)*.
4. Deploy. Vercel serves `index.html` automatically → your site is live at `https://<repo>.vercel.app`.
5. To get **demonteam.vercel.app** exactly: Project Settings → Domains → add `demonteam.vercel.app` (or rename the project to `demonteam`, which assigns it automatically).

Every `git push` after that redeploys automatically.

## What `vercel.json` does

Serves hardening headers on every response: HSTS, CSP, clickjacking block (`frame-ancestors 'none'`), nosniff, COOP/CORP, referrer strip. Don't remove it — it's the server-side half of the protection.

## Notes

- Hash routing (`#/pricing`, `#/admin`…) means **no rewrite rules needed** — works on any static host.
- Admin entrance: `#/admin` — first visit creates the owner account (no default password ships).
- Orders, claims and support tickets relay to the staff Discord webhook.
