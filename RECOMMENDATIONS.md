# GeoSpot v3 Improvement Ideas

This document captures possible enhancements for GeoSpot v3 based on a review of the current `index.html` implementation.

## Architecture & Code Organization
- **Modularize assets:** Externalize the inline CSS and JavaScript in `index.html` into dedicated files to improve caching, readability, and maintainability. The current file embeds several hundred lines of styles and logic directly in the HTML head and body. 【F:index.html†L8-L199】【F:index.html†L227-L657】
- **Introduce build tooling:** Adopt a lightweight bundler (e.g., Vite, Parcel) to transpile modern JavaScript, manage dependencies, and split vendor bundles such as Mapbox GL and Turf for quicker load times. This will also simplify future upgrades of Mapbox and other libraries.

## Performance & Loading Experience
- **Lazy-load non-critical audio:** Defer loading of large MP3 assets until they are needed to shorten the initial load path. Currently, every audio clip is eagerly instantiated on startup. 【F:index.html†L231-L279】
- **Provide offline caching:** Configure a service worker to cache GeoJSON, audio, and UI assets so users on slow or intermittent networks can continue playing without re-downloading resources each session.

## Gameplay & UX Enhancements
- **Add practice/custom rounds:** Allow players to configure the number of rounds or choose specific regions before starting a game, building on the existing difficulty selector. 【F:index.html†L205-L246】【F:index.html†L421-L507】
- **Improve accessibility:** Expose keyboard controls and focus indicators for critical buttons (Start, Exit, Tracker Back) and ensure dynamic announcements (e.g., country name, feedback) are surfaced to screen readers via `aria-live` regions. These controls are currently pointer-focused with limited ARIA support. 【F:index.html†L205-L270】【F:index.html†L355-L420】
- **Enhance tracker insights:** In tracker mode, surface statistics such as total visited/wishlist counts and add export/import options so travelers can share or back up their data. The legend already hints at richer state management that can support these features. 【F:index.html†L247-L356】【F:index.html†L357-L436】

## Visual & Thematic Polish
- **Provide theming options:** Offer a toggle between satellite and vector basemaps or allow pitch adjustments so players can choose between the current dramatic 3D look and a flatter atlas view. 【F:index.html†L490-L563】
- **Animate feedback events:** Extend the existing star explosion effect to highlight correct guesses on the map (e.g., pulse the country outline) and add subtle animations for streak milestones to reinforce progression. 【F:index.html†L161-L214】【F:index.html†L563-L620】

## Data & Internationalization
- **Localize UI strings:** Externalize visible strings (buttons, feedback messages) into a translation layer to support multi-language players; present copy is hard-coded in English. 【F:index.html†L200-L270】【F:index.html†L421-L620】
- **Augment geographic data:** Enrich `countries.geo.json` with alternative names or translations to improve answer matching and display for diverse audiences.

## Analytics & Social Features
- **Integrate progress persistence:** Store per-difficulty high scores and streaks in local storage or a backend to motivate repeat play and long-term skill tracking. 【F:index.html†L421-L507】
- **Enable sharing:** After a session, generate a summary image or shareable link that captures score, accuracy, and the countries missed to encourage friendly competition.

These ideas can be prioritized based on effort and impact to guide the GeoSpot v3 roadmap.
