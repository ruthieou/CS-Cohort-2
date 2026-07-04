# BCACC Course Home — auto-deploy to SiteGround

This repo holds the course landing page (`index.html`). Every push to `main`
automatically uploads it to SiteGround via FTPS.

## One-time setup

### 1. Create the repo
On github.com: New repository (private is fine), then drag the contents of
this folder into it (including the `.github` folder — enable "hidden files"
visibility if you don't see it after unzipping).

### 2. Create an FTP account on SiteGround
Site Tools → Site → FTP Accounts → Create:
- Note the **hostname** (e.g. `ftp.ruthunaegbu.com`), **username**, and **password**.
- Set the FTP account's path to the folder where the page should live
  (e.g. `public_html` for yoursite.com, or `public_html/course` for yoursite.com/course).

### 3. Add the credentials as repo secrets
GitHub repo → Settings → Secrets and variables → Actions → New repository secret:

| Secret name      | Value                                              |
|------------------|----------------------------------------------------|
| `FTP_SERVER`     | your FTP hostname, e.g. `ftp.ruthunaegbu.com`      |
| `FTP_USERNAME`   | the FTP username                                   |
| `FTP_PASSWORD`   | the FTP password                                   |
| `FTP_SERVER_DIR` | `./` (or a subfolder relative to the FTP account's path, ending in `/`) |

### 4. Test it
Repo → Actions tab → "Deploy to SiteGround" → Run workflow. Green check =
the page is live.

## Updating the site from then on

Replace `index.html` in the repo (drag the new file onto the repo page on
github.com and commit). The workflow uploads it to SiteGround automatically
within a minute or two.
