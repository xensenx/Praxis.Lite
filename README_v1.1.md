# Proxen v1.1 – Transparency & Trust Update

## Overview

Version 1.1 focuses entirely on **transparency, trust, and verifiability**. No new features were added. Instead, this update makes it trivially easy for cautious users to understand and verify exactly what Proxen does (and doesn't do) with their data.

---

## What Changed in v1.1

### 1. Pre-Initialization Transparency Block

**Location:** Landing page, before "Initialize System" button

**What it shows:**
- Exact AI model used (Gemma 3 27B IT)
- Exact API endpoint called (generativelanguage.googleapis.com)
- Data flow diagram (Your browser → Google API → Your browser)
- Explicit statement that Proxen does not receive, store, or process user data
- Confirmation that API key is stored locally only

**Why it matters:** Users can understand the system's architecture before making any commitment or providing any credentials.

---

### 2. Full Technical Details Modal

**Access:** "View Full Technical Details" button on landing page (no API key required)

**What it contains:**
- Complete data flow explanation
- List of what Proxen does NOT do (logging, storage, analytics, etc.)
- Local storage details (what's stored, where, how to verify)
- Verification instructions using browser DevTools
- Public source code links with deployment correspondence statement
- Creator contact information

**Why it matters:** Technically curious users can audit the claims without needing to initialize the system first.

---

### 3. Detailed API Key Scope Explanation

**Location:** API key entry screen

**What it shows:**
- Exact model accessed (Gemma 3 27B IT)
- Full API endpoint URL
- Purpose of key (inference only, no training/fine-tuning/storage)
- Key transmission path (browser → Google, never to Proxen)
- Key storage location (localStorage on device)
- Explicit recommendation to use restricted/project-specific keys

**Why it matters:** Users know exactly what their API key will be used for before providing it.

---

### 4. Public Source Code Access

**Locations:** 
- Landing page footer (link to GitHub repo)
- Technical details modal (repo + creator profile)
- Updated footer (creator GitHub link)

**What's provided:**
- Direct link to https://github.com/xensenx/Proxen
- Statement that deployed code corresponds to public repository
- Creator profile: https://github.com/xensenx

**Why it matters:** Users can verify claims by reading the source code themselves.

---

### 5. Privacy & Data Handling Page

**Access:** "Privacy & Data" button in landing page footer

**What it covers:**
- What data is stored (API key, username, tasks, conversation history)
- Where it's stored (browser localStorage on device only)
- What data is never collected (email, IP, analytics, device fingerprints, etc.)
- Third-party data sharing (direct to Google API, covered by Google's privacy policy)
- How to remove all data (Reset button, DevTools, or clear site data)

**Why it matters:** Plain language explanation without legal jargon or marketing speak.

---

### 6. Threat Model Documentation

**Access:** "Threat Model" button in landing page footer

**What it covers:**

**What Proxen DOES protect against:**
- Server breaches (no servers exist)
- Account database leaks (no accounts exist)
- Third-party tracking (no tracking scripts)
- Data mining (Proxen cannot access user data)
- Cross-device profiling (data never leaves device)

**What Proxen DOES NOT protect against:**
- Compromised browsers
- Malicious browser extensions
- Stolen or unlocked devices
- Network interception (despite HTTPS)
- Google API vulnerabilities

**Honest assessment:** Explicitly states the weakest links are device security, browser integrity, and Google's API security.

**Why it matters:** Users understand the real-world security boundaries of a local-first architecture.

---

### 7. Interactive Version & Changelog

**Access:** Click the "v1.1" text in the header

**What it shows:**
- Current version (v1.1)
- Complete changelog for v1.1 (transparency features)
- Original v1.0 feature list
- Planned improvements roadmap
- Note that roadmap is subject to change

**Why it matters:** Users can see what changed and what might change in the future.

---

### 8. Early-Stage Disclosure

**Location:** Landing page footer

**What it says:**
> "Early-Stage Disclosure: This is version 1.1 of an early-stage project. Transparency and verifiability are ongoing priorities. This app does not collect or transmit data to Proxen servers, but it cannot protect against compromised browsers, malicious extensions, or stolen devices."

**Why it matters:** Sets realistic expectations. No false claims of being "secure" or "private" — just factual statements about what the architecture does and doesn't provide.

---

## Design Principles for v1.1

### Tone Guidelines (Followed Throughout)

✅ **Do:**
- Use factual, precise language
- Say "does not" and "cannot" when accurate
- Assume the reader is skeptical and technically curious
- Provide verification paths
- Acknowledge limitations honestly

❌ **Don't:**
- Use hype or marketing language
- Make vague promises
- Use words like "secure," "safe," or "private" without qualification
- Hide limitations or edge cases

---

## Verification Instructions

Users can verify Proxen's behavior by:

1. **Network Monitoring:**
   - Open DevTools (F12) → Network tab
   - Interact with the app
   - Confirm all API requests go to `generativelanguage.googleapis.com`
   - Confirm no requests go to any Proxen-owned domains

2. **Source Code Review:**
   - Visit https://github.com/xensenx/Proxen
   - Read `app.js` to see API call implementation
   - Confirm no backend server code exists
   - Compare deployed code against repository

3. **Local Storage Inspection:**
   - Open DevTools (F12) → Application → Local Storage
   - Inspect `focus_local_state` key
   - Confirm it contains only: API key, username, tasks, conversation history
   - Confirm nothing else is stored

4. **No External Requests:**
   - Block all domains except `generativelanguage.googleapis.com`
   - Confirm app still functions normally
   - This proves no other services are being called

---

## File Changes Summary

### `index.html`
- ✅ Updated version to v1.1
- ✅ Made version number clickable
- ✅ Added transparency block on landing page (pre-initialization)
- ✅ Added detailed API key scope explanation
- ✅ Added footer links to Privacy, Threat Model, and Source Code
- ✅ Added early-stage disclosure in footer
- ✅ Added Technical Details modal (full data flow, verification instructions)
- ✅ Added Privacy modal (plain language data handling)
- ✅ Added Threat Model modal (protections and limitations)
- ✅ Added Changelog modal (version history and roadmap)
- ✅ Updated footer with creator GitHub link

### `app.js`
- ✅ Added DOM references for new modals
- ✅ Added version button click handler
- ✅ Renamed `openTestModal` to `showTestModal` for consistency
- ✅ Added `showTechnicalDetails()` / `closeTechnicalModal()`
- ✅ Added `showPrivacy()` / `closePrivacyModal()`
- ✅ Added `showThreatModel()` / `closeThreatModal()`
- ✅ Added `showChangelog()` / `closeChangelogModal()`
- ⚪ No changes to core functionality or API integration

### `styles.css`
- ✅ Added `.header-version.clickable` styles
- ✅ Added `.transparency-block` and related styles
- ✅ Added `.api-scope-block` and related styles
- ✅ Added `.link-button` and `.inline-link` styles
- ✅ Added `.footer-links` and `.footer-link` styles
- ✅ Added `.modal-large` for larger content modals
- ✅ Added `.technical-content`, `.tech-section`, `.tech-diagram` styles
- ✅ Added `.privacy-section` and related styles
- ✅ Added `.threat-section` and related styles
- ✅ Added `.changelog-section` and related styles
- ✅ Added mobile responsiveness for new elements
- ⚪ No changes to existing component styles

---

## What Stayed the Same

All core functionality from v1.0 remains unchanged:

- ✅ Gemma 3 27B IT integration via Google API
- ✅ Natural language task management
- ✅ Task creation, completion, deletion via conversation
- ✅ Smart intent detection
- ✅ Inline task changes with visual connections
- ✅ Momentum-aware AI responses
- ✅ Suggestion pills
- ✅ Local-first architecture
- ✅ No servers, no accounts, no tracking
- ✅ API key testing modal

**Zero breaking changes.** Existing functionality is 100% preserved.

---

## Testing Checklist

### Transparency Features
- [x] Pre-initialization transparency block displays correctly
- [x] All information is accurate and specific
- [x] Technical details modal opens without requiring API key
- [x] API key scope explanation shows before key entry
- [x] Privacy modal accessible from footer
- [x] Threat model modal accessible from footer
- [x] Changelog modal opens when version number is clicked
- [x] Source code links work correctly
- [x] Early-stage disclosure displays in footer

### Existing Functionality (Regression Tests)
- [x] API key entry and validation works
- [x] API key testing modal works
- [x] Name entry works
- [x] Workspace initializes correctly
- [x] Task creation works
- [x] Task completion works
- [x] Task deletion works
- [x] AI responses maintain personality
- [x] Conversation history preservation
- [x] Reset system functionality
- [x] Mobile responsiveness

### User Experience
- [x] All modals close correctly
- [x] All buttons respond to clicks
- [x] No broken links
- [x] Consistent visual design
- [x] Clear information hierarchy
- [x] Readable on mobile devices

---

## User Impact

### For Cautious Users
- Can now verify all claims before initializing
- Have clear verification paths using DevTools
- Understand exact data flow and storage
- Know the threat model and limitations

### For Technical Users
- Can audit source code on GitHub
- Can monitor network requests
- Can inspect localStorage contents
- Can verify deployment corresponds to repository

### For Privacy-Conscious Users
- Clear statement of what's collected (locally) and what's not
- No ambiguity about data transmission
- Easy path to remove all data
- Understanding of Google API privacy implications

### For All Users
- No feature regression
- No breaking changes
- Same functionality with added transparency
- Clear roadmap for future updates

---

## Philosophy Behind v1.1

Early-stage projects often make bold claims about privacy and security without providing verification paths. v1.1 takes the opposite approach:

1. **Assume skepticism:** Users should be able to verify claims, not just trust them
2. **Acknowledge limitations:** Be honest about what the architecture cannot protect against
3. **Provide tools:** Give users DevTools instructions and source code access
4. **No marketing speak:** Use precise, factual language without hype
5. **Progressive disclosure:** Basic info on landing page, full details in modals

The goal is not to convince users that Proxen is "secure" or "private" — it's to give them the information they need to make that determination themselves.

---

## Credits

**Original concept and implementation:** xensenx  
**v1.1 Transparency Update:** Focused on trust, verifiability, and honest communication about capabilities and limitations.

**Source Code:** https://github.com/xensenx/Proxen  
**Creator:** https://github.com/xensenx

Built with intentionality, not features.

---

## Installation (Unchanged)

1. Open `index.html` in a modern browser
2. Review transparency information (new in v1.1)
3. Provide Google API key (with new detailed scope explanation)
4. Enter your name
5. Start talking

**No build process. No dependencies. Just open and use.**

---

## Next Steps

Future versions will continue to prioritize transparency and verifiability while adding:
- Enhanced error recovery
- Task scheduling features  
- Export functionality
- Improved mobile experience
- Optional categorization

All changes will be documented in the changelog with the same level of transparency as v1.1.
