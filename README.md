# Pushpa Sharma — Portfolio

Single-file portfolio site (`index.html` + `Pushpa_Sharma_Resume.pdf`). No build step, no dependencies.

## Deploy to GitHub Pages

1. Create a new repo on GitHub. For the cleanest URL, name it exactly:
   `pushpa-sharma-31.github.io`
   (Any other repo name also works — the site will live at `https://pushpa-sharma-31.github.io/<repo-name>/`.)
2. Upload both files (`index.html` and `Pushpa_Sharma_Resume.pdf`) to the repo root — either drag-and-drop on github.com ("Add file → Upload files") or:
   ```bash
   git init
   git add index.html Pushpa_Sharma_Resume.pdf README.md
   git commit -m "Portfolio site"
   git branch -M main
   git remote add origin https://github.com/pushpa-sharma-31/pushpa-sharma-31.github.io.git
   git push -u origin main
   ```
3. In the repo: **Settings → Pages → Source: Deploy from a branch → main / (root) → Save**.
4. Wait a minute or two. The site goes live at `https://pushpa-sharma-31.github.io/`.

## Features & how they work

- **Dark / bright theme** — the moon/sun button in the nav switches themes; the choice is saved in the browser, and first-time visitors get whichever matches their device setting.
- **Download resume** — the buttons link to `Pushpa_Sharma_Resume.pdf` with a `download` attribute. To update the resume later, just replace that file (keep the same name).
- **Call me** — the "Call" buttons use `tel:+918197709916`, which opens the dialer on phones (and Skype/FaceTime on desktops).
- **Contact form → email** — the form posts to [FormSubmit](https://formsubmit.co) (free, no account, works on static sites) and delivers messages to `pushpa2431sharma@gmail.com`.
  - **One-time activation:** the very first time someone submits the form on the live site, FormSubmit emails you a confirmation link. Click it once and all future messages land straight in your inbox. Tip: after deploying, submit a test message yourself to trigger this.
  - If sending ever fails (e.g. offline), the form falls back to opening the visitor's email app pre-filled.

## Editing content

Everything lives in `index.html` — search for the section you want (`about`, `skills`, `experience`, `education`, `contact`) and edit the text directly.

## Admin portal

`admin.html` is a hidden owner-only editor. It's not linked from the site — open it directly:
`https://bablu-singh.github.io/pushpa-portfolio/admin.html`

**How access control works:** the page itself is public (static hosting can't hide files), but it can do nothing without a GitHub token that has **write access to this exact repo**. On connect it verifies push permission via the GitHub API and refuses otherwise. Saving = a commit to `content.json`; GitHub Pages redeploys automatically (~1 min).

**One-time setup — create your token:**
1. Go to github.com → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token.
2. Repository access: **Only select repositories** → choose `pushpa-portfolio`.
3. Permissions → Repository permissions → **Contents: Read and write**. Nothing else.
4. Generate, copy, and paste it into the admin page. Optionally tick "remember for this session".
5. Never commit the token to the repo or share it. If it leaks, revoke it on GitHub — that instantly locks the portal.

**What's editable:** hero text and rotating role words, availability pill, tagline, contact details (email/phone also re-wire the buttons and the contact form), about paragraphs, stats, skill groups, the full experience timeline (add/remove roles), education, and achievements. The site reads `content.json` at load; if the file is ever missing, the page falls back to its built-in content.
