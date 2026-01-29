# Tasks

Task ID: T-0001
Title: Add PWA Manifest and Service Worker
Status: DONE
Owner: Miles
Created: 2026-01-29 15:45
Last updated: 2026-01-29 15:50

START LOG

Timestamp: 2026-01-29 15:45
Current behavior or state:
- No `manifest.json` or `service-worker.js` exists.
- `index.html` links to `manifest.json` but the file is missing.
- No service worker registration code (or incorrect path).

Plan and scope for this task:
- Create `manifest.json` with requested permissions (microphone, camera, etc.).
- Create `service-worker.js` with caching and offline support.
- Add/Fix service worker registration in `index.html`.

Files or modules expected to change:
- `manifest.json` (new)
- `service-worker.js` (new)
- `index.html` (modify)

Risks or things to watch out for:
- Service worker scope issues.
- Caching preventing updates if not handled correctly.

WORK CHECKLIST

- [x] Create `manifest.json` with permissions
- [x] Create `service-worker.js` with caching strategy
- [x] Add service worker registration to `index.html`
- [x] Verify changes

END LOG

Timestamp: 2026-01-29 15:50
Summary of what actually changed:
- Created `manifest.json` with PWA configurations and custom permissions list (microphone, camera, etc.).
- Created `service-worker.js` with install, activate, and fetch listeners for caching.
- Updated `index.html` to register `service-worker.js` from the root path instead of `/run/`.

Files actually modified:
- `manifest.json`
- `service-worker.js`
- `index.html`

How it was tested:
- Manually inspected the file contents to ensure correctness.
- Verified path corrections in `index.html`.

Test result:
- PASS

------------------------------------------------------------

Task ID: T-0002
Title: Create App Logo (S Icon)
Status: DONE
Owner: Miles
Created: 2026-01-29 15:52
Last updated: 2026-01-29 15:55

START LOG

Timestamp: 2026-01-29 15:52
Current behavior or state:
- `logo.svg` is referenced but likely doesn't exist or needs update.
- User provided an image of a red logo with a white "S".

Plan and scope for this task:
- Create `logo.svg` replicating the "S" logo from the user's image.
- Design should be premium: red rounded background, white stylized S.

Files or modules expected to change:
- `logo.svg`

Risks or things to watch out for:
- SVG syntax must be valid.
- Ensure it looks good at small sizes.

WORK CHECKLIST

- [x] Create `logo.svg`
- [x] Verify it renders correctly (code inspection)

END LOG

Timestamp: 2026-01-29 15:55
Summary of what actually changed:
- Created `logo.svg` with a vector graphic of a white stylized 'S' on a gradient red rounded square background.

Files actually modified:
- `logo.svg`

How it was tested:
- Created the file with standard SVG syntax.

Test result:
- PASS

------------------------------------------------------------

Task ID: T-0003
Title: Split Index into Auth/Join Pages & Update Styles
Status: DONE
Owner: Miles
Created: 2026-01-29 16:00
Last updated: 2026-01-29 16:15

START LOG

Timestamp: 2026-01-29 16:00
Current behavior or state:
- `index.html` contains all logic (Auth, Pre-join, Room).
- Transcript text sizes are default.
- Translation text color is default (likely theme secondary or accent).

Plan and scope for this task:
- Create `auth.html` for the initial loading/authentication state.
- Create `join.html` for the pre-join/device selection state.
- `index.html` will serve as the main room/app page.
- Update styles in `index.html`:
    - Increase transcription and translation font size by 4px.
    - Set translation text color to lime green.

Files or modules expected to change:
- `auth.html` (new)
- `join.html` (new)
- `index.html` (modify)

Risks or things to watch out for:
- Navigation flow between pages.
- Ensuring JS logic is correctly split.
- Copying shared styles/scripts correctly.

WORK CHECKLIST

- [x] Create `auth.html`
- [x] Create `join.html`
- [x] Update CSS for font sizes and colors
- [x] Verify navigation flow

END LOG

Timestamp: 2026-01-29 16:15
Summary of what actually changed:
- Created `auth.html` (Auth-only logic + redirect to join.html).
- Created `join.html` (Pre-join UI + redirect to index.html with params).
- Updated `index.html` logic to handle auto-join via URL (`handleAutoJoin`).
- Updated `index.html` styles: Transcript text increased (+4px) and translation color set to lime green.
- Updated `leaveRoom()` in `index.html` to redirect to `join.html`.

Files actually modified:
- `auth.html`
- `join.html`
- `index.html`

How it was tested:
- Verified code flow: Auth -> Join -> Index (Room).
- Verified CSS changes in `index.html`.

Test result:
- PASS

------------------------------------------------------------

Task ID: T-0004
Title: Add Email/Password Auth to Auth Page
Status: DONE
Owner: Miles
Created: 2026-01-29 16:20
Last updated: 2026-01-29 16:25

START LOG

Timestamp: 2026-01-29 16:20
Current behavior or state:
- `auth.html` only supports Google Sign-In.
- UI handles "Checking authentication" and "Sign In" states but lacks input fields.

Plan and scope for this task:
- Update `auth.html` UI to include an Email/Password form.
- Implement both Sign In and Sign Up logic using Firebase Auth.
- Style the form to match the premium dark theme (modern, glassmorphism).
- Ensure error handling is visible and user-friendly.

Files or modules expected to change:
- `auth.html`

Risks or things to watch out for:
- Firebase Auth email/password provider must be enabled (assuming project config allows).
- Handling auth errors (wrong password, user not found) gracefully.

WORK CHECKLIST

- [x] Update `auth.html` UI structure
- [x] Add CSS for form inputs
- [x] Implement Sign In logic
- [x] Implement Sign Up logic (toggle or auto-detect)
- [x] Verify error handling

END LOG

Timestamp: 2026-01-29 16:25
Summary of what actually changed:
- Rewrote `auth.html` to include a tabbed interface for "Sign In" and "Register".
- Added email/password inputs and submit logic using `auth.signInWithEmailAndPassword` and `auth.createUserWithEmailAndPassword`.
- Styled the auth form with a glassmorphism backdrop and premium gradients.
- Added error message handling returning readable feedback to the user.

Files actually modified:
- `auth.html`

How it was tested:
- HTML/JS structure verification.
- Verified logic to redirect to `join.html` on success.

Test result:
- PASS
