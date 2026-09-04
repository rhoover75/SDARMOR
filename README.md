# SD-ARMOR site — deploy notes (no terminal needed)

Plain static HTML/CSS/JS. No build step, no framework — every page links the
same `assets/style.css` and `assets/site.js`, so editing colors, type, or the
nav happens once and applies everywhere.

## Files

- `index.html` — home / landing page
- `research.html`, `leadership.html`, `outreach.html`, `partners.html`, `contact.html`
- `assets/style.css`, `assets/site.js` — shared styles and the mobile-nav script
- `assets/logo.png`, `assets/logo-mark.png` — full lockup and compact mark (transparent PNG;
  both are placed on a white "plate" in the CSS so the navy/orange art keeps contrast in dark mode)
- `assets/favicon.ico`, `assets/favicon-32.png`, `assets/favicon-192.png`, `assets/apple-touch-icon.png` —
  browser tab / bookmark / home-screen icons, generated from the compact mark

`impact.html` is intentionally not included in this package — it's unlinked from
the live site and left out of the repo so the funding figures aren't sitting in
a public GitHub repo even as an orphaned page.

## Step 1 — create the repo (github.com, logged in as rhoover75)

1. Go to **github.com/new**.
2. Repository name: `sd-armor-site` (or anything you like — it doesn't have to
   match the site's name).
3. Set it to **Public** — free GitHub accounts can only serve Pages sites from
   a public repo. That's fine here: the repo only ever holds these static
   files, nothing internal.
4. Leave "Initialize with a README" **unchecked** (this zip already has one).
5. Click **Create repository**.

## Step 2 — upload the files (drag and drop, no command line)

1. On the new, empty repo page, click **"uploading an existing file"** —
   it's a plain link right there on the page.
2. Unzip `sd-armor-site.zip` on your computer, then drag the files into the
   upload box: the 6 `.html` files, `README.md`, and the whole `assets`
   folder. Dragging the `assets` folder in (rather than the files inside it
   one at a time) makes GitHub recreate that subfolder automatically.
3. Scroll down, type a commit message like "Initial site," click
   **Commit changes**.

## Step 3 — turn on GitHub Pages

1. In the repo, click the **Settings** tab, then **Pages** in the left sidebar.
2. Under "Build and deployment," set **Source** to **Deploy from a branch**,
   **Branch: main**, folder **/ (root)** → **Save**.
3. Wait a minute or two, refresh that same Settings → Pages screen — it will
   show your live URL, something like `https://rhoover75.github.io/sd-armor-site/`.

## Making updates later

Whenever I hand you an updated file:

1. Go to the repo on github.com.
2. Click **Add file → Upload files** (top right of the file listing), or just
   drag the new file onto that page.
3. Upload the replacement file(s) with the exact same name as before — GitHub
   will overwrite the old version.
4. Commit.

Pages redeploys automatically within a few seconds of every commit. No other
step, and no command line at any point.

## Custom domain (optional, whenever you're ready)

1. Buy/point a domain (e.g. `sd-armor.org`).
2. In Settings → Pages, type the domain into the **Custom domain** field and
   save — GitHub creates the required `CNAME` file in the repo for you.
3. At your domain registrar, point DNS at GitHub Pages:
   - Apex domain (`sd-armor.org`): four **A** records to
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `www` subdomain: a **CNAME** record to `rhoover75.github.io`
4. Back in Settings → Pages, once DNS has propagated, check **Enforce HTTPS**.
   GitHub issues the SSL certificate automatically — no cost, no manual renewal.

## If you ever want the command-line version instead

Entirely optional — the steps above are the whole workflow. But if you (or
someone helping you) later install `git`, the equivalent is:

```bash
cd sd-armor-site
git init && git add . && git commit -m "Initial SD-ARMOR site"
git branch -M main
git remote add origin https://github.com/rhoover75/sd-armor-site.git
git push -u origin main
```

and for later updates: `git add .`, `git commit -m "..."`, `git push`.
