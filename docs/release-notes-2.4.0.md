# Mechvibes 2.4.0

Mechvibes 2.4.0 is the first stable release of the 2.4 runtime foundation. Every soundpack (v1, v2, and v3) now runs on a single low-latency Web Audio engine; the legacy Howler engine that shipped as a beta rollback path has been removed.

## Highlights

- Promoted the unified Web Audio engine to the only audio path for v1, v2, and v3 soundpacks. The Howler-based v1/v2 fallback and its `MECHVIBES_LEGACY_AUDIO` environment switch were removed after the beta soak proved parity.
- Soundpack v3 layers, weighted or round-robin sample selection, pitch variation, envelopes, configurable preload behavior, optional SHA-256 integrity checks, and author/license metadata.
- Decoded-sample caching, shared buffers, bounded LRU eviction, voice budgeting, and input-latency metrics.
- Selectable audio outputs with fallback to the system default when a saved device is unavailable.
- In-app stable/beta update channel with explicit consent before download or installation.
- Refresh, import, open-folder, and delete controls for local soundpacks.
- Dark theme and improved keyboard accessibility for critical controls.

## Security

- Major-bumped `electron-builder` from 24.13.3 to 26.15.3 to pull in patched transitive dependencies (node-tar, `@xmldom/xmldom`, `form-data`, `app-builder-lib`, `dmg-builder`, `ejs`, `lodash`, `cross-spawn`, `@tootallnate/once`, and `glob`).
- Applied non-breaking fixes for the remaining top-level `minimatch` and `brace-expansion` ReDoS advisories.
- `npm audit` reports zero vulnerabilities.
- Removed the redundant `yarn.lock`; `package-lock.json` is the single authoritative lockfile used by CI (`npm ci`).

## Verification

- Node.js 22.22.0 syntax, soundpack, test, typecheck, and lint gates pass (`npm run verify`).
- 29 of 29 automated tests pass, including the forced Windows renderer path.
- The `package.json` `build` configuration is accepted unchanged by electron-builder 26.
- Runtime dependency audit reports zero vulnerabilities.

## Scope and limitations

- This release targets **Windows x64 only**. Windows arm64, macOS, and Linux are out of scope for 2.4.0.
- Builds are unsigned by explicit project decision and may trigger Microsoft SmartScreen warnings. Broad stable distribution should wait for OV, EV, or Azure Trusted Signing.
