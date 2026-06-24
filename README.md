# Rent Manager Pro — Android App Setup

## What's in this package
- `index.html` — the app itself (login page → dashboard, tenants, payments, receipts, reminders)
- `manifest.json` — tells Android "this is an installable app" (name, icon, colors)
- `sw.js` — service worker, lets the app work fully **offline** once installed
- `icon-192.png` / `icon-512.png` — the app icon you'll see on your home screen

Default login: **admin / admin123** (change it in Settings after logging in)

---

## Step 1 — Put it online (required once)
Android needs the files served over **https** to install them as an app — it can't
install directly from a file on your computer. GitHub Pages is free and takes 5 minutes:

1. Go to **github.com** → sign up (free) if you don't have an account
2. Click **+** → **New repository** → name it `rent-manager` → set **Public** → **Create repository**
3. Click **"uploading an existing file"**
4. Drag in **all 5 files** from this package (`index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`) — keep them all in the same top-level folder, don't rename `index.html`
5. Click **Commit changes**
6. Go to **Settings → Pages** (left sidebar) → under **Branch** select `main` → **Save**
7. Wait 1–2 minutes, then your app is live at:
   `https://YOUR-USERNAME.github.io/rent-manager/`

---

## Step 2 — Install it on your Android phone
1. Open that URL in **Chrome** on your Android phone
2. Log in once (admin / admin123)
3. You'll see a small banner: **"📲 Tap here to install this app on your phone"** — tap it
   - If you don't see it, tap the **⋮** menu in Chrome → **"Add to Home screen"** / **"Install app"**
4. Confirm **Install**
5. A **Rent Manager Pro** icon now appears on your home screen, just like any other app
6. Opening it launches full-screen, with no browser address bar — and it keeps working even with **no internet**, since your data is stored on the phone itself

---

## About the database
- All tenant and payment data lives in the phone's local app storage (not on any server)
- Nothing is uploaded anywhere — it's private to your device
- **Backup regularly**: open the app → **Database** tab → **Download Backup (.json)**. Save that file somewhere safe (Google Drive, email to yourself, etc.)
- To move data to a new phone: install the app there too, then use **Database → Import & Restore** with that backup file

---

## Want a real Play Store APK instead of a home-screen shortcut?
Once your app is live on GitHub Pages, you can turn it into a real installable
`.apk`/`.aab` file (good enough to even publish on the Play Store) for free using
**PWABuilder**:

1. Go to **pwabuilder.com**
2. Paste in your GitHub Pages URL (e.g. `https://YOUR-USERNAME.github.io/rent-manager/`)
3. Click **Start** → it will detect the manifest and service worker automatically
4. Go to the **Android** package option → **Generate Package**
5. Download the `.apk` — you can install that directly on any Android phone (you may need to allow "install from unknown sources" once), or upload the `.aab` to Google Play Console if you want to publish it properly

This step is optional — the home-screen install in Step 2 already behaves like a real
app (own icon, full-screen, offline). PWABuilder is only needed if you specifically want
an `.apk` file or a Play Store listing.
