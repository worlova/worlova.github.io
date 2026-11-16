# Valentina Orlova — portfolio

The published build of Valentina's portfolio: one `index.html`, its fonts, images and videos, and the CV. No build step, no dependencies, no server code — any static host will serve it as it is.

## Publishing it on GitHub Pages

1. **Create the repository.** On GitHub, new repository, named exactly `worlova.github.io`, public, with no README, .gitignore or licence (this folder already has its first commit).
2. **Push this folder:**

   ```bash
   cd ~/Desktop/valentina-orlova-portfolio
   git remote add origin https://github.com/worlova/worlova.github.io.git
   git branch -M main
   git push -u origin main
   ```

3. **Turn Pages on.** Repository → Settings → Pages → Build and deployment → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`. Save.
4. Wait a minute or two. The site is then at `https://worlova.github.io`, and at `https://www.worlova.com` once the DNS below is in place.

### www.worlova.com

The `CNAME` file in this folder already holds `www.worlova.com`, so GitHub serves the site there once the DNS is pointed at it.

At the registrar for `worlova.com`, add:

   | Type | Name | Value | What it does |
   | --- | --- | --- | --- |
   | CNAME | `www` | `worlova.github.io.` | the site itself |
   | A | `@` | `185.199.108.153` | so `worlova.com` redirects to `www` |
   | A | `@` | `185.199.109.153` | |
   | A | `@` | `185.199.110.153` | |
   | A | `@` | `185.199.111.153` | |

(The four A records are optional and only make the bare domain redirect to the www one. If your registrar offers ALIAS or ANAME on the root, point that at `worlova.github.io.` instead.)

Then: repository → Settings → Pages → Custom domain → `www.worlova.com` → Save, and tick **Enforce HTTPS** once the certificate is issued, usually within the hour. DNS changes can take anywhere from minutes to a day to spread.

## What is in here

| | |
| --- | --- |
| `index.html` | the whole site — markup, styles, and the script that renders the Home page, the case studies and the CV |
| `img/` | case study images and videos, the Home card thumbnails, the company logos, the About portrait |
| `fonts/` | Inter and Cormorant Garamond, self-hosted, so nothing is requested from Google |
| `Valentina-Orlova-Resume.pdf` | the CV, opened in the CV tab and downloadable from it |
| `.nojekyll` | stops GitHub Pages from running Jekyll over the files |

Every path in the page is relative, so the site works at a domain root, in a subfolder, or opened straight from disk.

## Editing it later

The site's text lives in one place in `index.html`: the `PROJECTS` array (one entry per case study) and the `SAVED_COPY` object just below it, which holds the case study copy as it was last edited in the draft and is merged over `PROJECTS` when the page loads. Edit either, commit, push — Pages redeploys in about a minute.

`SITE` at the top of the script holds the name, the contact links, the About card, and `editMode`. **`editMode` is `false` here and should stay that way**: the inline editor and its database only exist in the draft inside Claude.
