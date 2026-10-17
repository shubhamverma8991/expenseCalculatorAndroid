# Kharcha

Monthly income and expense tracker for Android, in ₹.

- Summary, Entries and History screens (bottom bar)
- Month can start on your salary day (Settings ⚙)
- Custom date range in History
- Export to JSON (share to Drive, Files, WhatsApp…)
- Daily backup after 1:00 am, also saved to `Documents/Kharcha`, with restore

All data stays on the phone.

## One-time setup: signing key

The APK is signed with your own key, stored in GitHub Secrets (never in the code).
In this repo go to **Settings → Secrets and variables → Actions → New repository secret** and add:

| Name | Value |
| --- | --- |
| `KEYSTORE_BASE64` | contents of `keystore-base64.txt` |
| `KEYSTORE_PASSWORD` | contents of `keystore-password.txt` |

Keep `kharcha.keystore` and the password somewhere safe (e.g. Google Drive). Without the same key,
a future version can't install over the old one, and uninstalling first deletes your data.

## Get the APK

Every push to `main` builds the app with GitHub Actions (or run it by hand: **Actions → Build Android APK → Run workflow**).
Open **Releases**, download `Kharcha.apk` on your phone and install it
(allow "Install unknown apps" for your browser or Files app when asked).

## Change the app

The whole app is `www/index.html`. Edit it, push to `main`, and a new APK appears in Releases.

## Build on your computer (optional)

Needs Node 22, Java 21 and Android Studio.

```bash
npm install
npx cap add android
npx capacitor-assets generate --android
npx cap sync android
npx cap open android   # then Run ▶ in Android Studio
```
