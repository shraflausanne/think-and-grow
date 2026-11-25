# Setup instructions for Claude Code

You are setting up "Think and Grow", a small personal goals web app, so its owner can install it on an iPhone home screen and use it without Claude. The app is finished. Your job is only to publish it on GitHub Pages and confirm it works. Do not change the app's design or features.

## What is in this folder

- `index.html`: the whole app (HTML, CSS and JavaScript in one file). No build step, no dependencies.
- `manifest.webmanifest`: app name, colours and icons for "Add to Home Screen".
- `icons/apple-touch-icon.png` (180 px), `icons/icon-192.png`, `icons/icon-512.png`: home screen icons.
- `README.md`: a short note for the owner.
- This file.

The app saves all data in the browser's `localStorage` on the phone. There is no server, no account and no API key. Nothing needs configuring.

## Steps

1. **Repository.**
   - If you can create repositories: create a new **public** GitHub repository named `think-and-grow` under the owner's account (`gh repo create think-and-grow --public`).
   - If you cannot: stop and ask the owner to create an empty public repository named `think-and-grow` on github.com, then attach it to this session.
   - It must be public: GitHub Pages on a private repository needs a paid plan.

2. **Files.** Put every file from this folder at the **root** of the repository, keeping the `icons/` folder as it is. Commit to the `main` branch with the message `Add Think and Grow app` and push.

3. **Turn on GitHub Pages** (deploy from the `main` branch, root folder).
   - Try the API first:
     `gh api -X POST repos/OWNER/think-and-grow/pages -f "source[branch]=main" -f "source[path]=/"`
     (replace OWNER with the GitHub username; if it answers that Pages already exists, that is fine).
   - If you have no permission for that call, tell the owner to do it by hand, in these exact words:
     "On github.com open the think-and-grow repository, tap Settings, then Pages. Under Build and deployment, set Source to Deploy from a branch, Branch to main, folder to / (root), and tap Save."

4. **Wait and check.** GitHub usually takes one to three minutes to publish. The address will be:
   `https://OWNER.github.io/think-and-grow/`
   If you can, check the build with `gh api repos/OWNER/think-and-grow/pages/builds/latest` until `status` is `built`. Do not report success before that, or before the owner confirms the page opens.

5. **Give the owner these iPhone steps**, with the real address filled in:
   1. Open the address in **Safari** (not Chrome or another browser: only Safari can add it to the home screen as an app on most iPhones).
   2. Tap the **Share** button, then **Add to Home Screen**, then **Add**.
   3. Open the app from the new gold icon.
   4. Type a goal, wait for the pill at the top right to say **Saved on this phone**, close the app fully, reopen it, and check the goal is still there.

## Rules

- Do not edit `index.html`, the icons or the manifest unless something is broken. If something is broken, say what and ask before changing it.
- Do not add analytics, trackers, frameworks, a build step or a backend.
- Do not commit anything else (no secrets, no `.env`).
- Tell the owner plainly that the data lives only on that phone, inside the home screen app. Deleting the app or clearing Safari's website data erases it, and it does not sync to other devices.
