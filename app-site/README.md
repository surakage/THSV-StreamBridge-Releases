# app.slothbloom.com

The StreamBridge pages (Setup Wizard, Control Panel, Stream info, Jukebox remote) as plain files, served
from `https://app.slothbloom.com`. Opened there, they connect to StreamBridge running on the visitor's own
PC after the browser is paired with a code shown on that PC. No stream data passes through this site.

- `public/` is generated. Do not edit it by hand. The **Publish app.slothbloom.com pages** workflow rebuilds
  it from a release tag of the source repository (`npm run site:bundle` there) and commits the result.
- `wrangler.jsonc` describes the Cloudflare Worker `streambridge-app`, which only serves these files.
  Cloudflare deploys it whenever `main` changes (Workers Builds, root directory `app-site`).
- StreamBridge accepts these pages from `https://app.slothbloom.com` only, and only after the streamer
  turns on **Open StreamBridge from slothbloom.com** in the Wizard on their PC.
