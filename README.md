# NeleGo — VS Code edition

Karnataka tourism and heritage, with the same nature theme, glass panels, photographs, interactive map and latest hero refinements as the published NeleGo site.

This package is organised for reading, editing and running on your own computer. The local backend uses **Node.js + Express + SQLite**. The published Sites version uses a Cloudflare Worker and D1; this export replaces that hosting-specific setup while keeping the visitor experience and API behaviour.

## Start here

1. Install **Node.js 24 or newer** from [nodejs.org](https://nodejs.org/en/download). npm is included. Restart VS Code after installation.
2. Extract the ZIP. Open the **NeleGo folder containing `package.json`** in VS Code, or double-click `NeleGo.code-workspace`.
3. In VS Code, choose **Terminal → New Terminal**.
4. Run these commands from that folder:

```sh
npm install
npm run dev
```

5. Open **http://localhost:5173** in your browser.

The command starts the frontend and backend together. The SQLite database is created automatically. No API key, database account or `.env` file is required. Press **Ctrl+C** in the terminal when you finish.

On Windows, if PowerShell blocks `npm.ps1`, use `npm.cmd install` and `npm.cmd run dev` in the same terminal. You do not need to change PowerShell's security settings.

## Where is everything?

| Folder or file                                                     | What you edit here                                                              |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| [frontend/src/App.tsx](frontend/src/App.tsx)                       | The order of the homepage sections                                              |
| [frontend/src/sections](frontend/src/sections)                     | Hero, destination cards, heritage, map, culture and travel-care sections        |
| [frontend/src/dialogs](frontend/src/dialogs)                       | Destination guides, saved journey, observation form and information dialogs     |
| [frontend/src/components](frontend/src/components)                 | Shared logo, header, footer, modal, map and notifications                       |
| [frontend/src/hooks/useNeleGo.ts](frontend/src/hooks/useNeleGo.ts) | Frontend state, search, bookmarks and form submissions                          |
| [frontend/src/styles](frontend/src/styles)                         | Separate, named CSS files for each part of the design                           |
| [frontend/public/images](frontend/public/images)                   | All ten local photographs                                                       |
| [backend/data/destinations.json](backend/data/destinations.json)   | Destination history, coordinates, nearby places, culture, food and access notes |
| [backend/routes](backend/routes)                                   | API behaviour for destinations, saved places and observations                   |
| [backend/schema.sql](backend/schema.sql)                           | Database table definitions                                                      |
| `backend/storage/nelego.sqlite`                                    | Your local saved places and observations; created when the backend starts       |
| [tests/api.test.mjs](tests/api.test.mjs)                           | Backend integration tests using temporary databases                             |

For a guided reading order, open **[docs/CODE_GUIDE.md](docs/CODE_GUIDE.md)**. For setup problems, open **[docs/SETUP.md](docs/SETUP.md)**.

## Useful commands

| Command          | Result                                                           |
| ---------------- | ---------------------------------------------------------------- |
| `npm run dev`    | Start both servers with automatic reload while editing           |
| `npm run check`  | Check frontend TypeScript                                        |
| `npm test`       | Check API search, validation, persistence and visitor separation |
| `npm run build`  | Create the production frontend in `dist/`                        |
| `npm start`      | Serve the built frontend and API at http://localhost:3001        |
| `npm run format` | Format your authored files with Prettier                         |

For a production-style local run:

```sh
npm run build
npm start
```

Use **http://localhost:3001** for that run. The development address is **5173**; the built application's address is **3001**.

## Features included

- Eight complete destination guides: Hampi, Coorg, Gokarna, Chikkamagaluru, Mysuru, Belur & Halebidu, Pattadakal and Badami.
- Search by place, district, Kannada name, alternate spelling, category or region.
- Leaflet + OpenStreetMap with custom pins, nearby stops, zoom and reset controls.
- Culture and food stories, linked references, seasons, access notes and heritage information.
- Saved journeys that survive a backend restart, plus downloadable travel notes.
- Validated heritage observations with a receipt and per-browser submission limit.
- Responsive navigation, keyboard-friendly dialogs and reduced-motion support.
- Corrected tagline: **ONE KARNATAKA. MANY WORLDS.** The hero arrow starts beside “matters” and ends above the white search panel.

## A few details to understand

Saved places belong to the browser identified by a random HttpOnly cookie. This local edition does not include account login or cross-device synchronisation. Observation records stay in this project's database and are not forwarded to heritage authorities. Search uses the included curated catalog rather than a general worldwide place-search service.

Photographs and Leaflet files are included. Map tiles and Google Fonts require an internet connection. Photo credits and licences are on `/credits` and in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md). Destination information was reviewed on 8 November 2026; live closures and opening hours are not monitored.

This source export is independent of the hosted Site: editing or running it does not update the published NeleGo website.
