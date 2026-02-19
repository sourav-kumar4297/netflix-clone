# Netflix Clone (Portfolio)

A Netflix-style movie and TV browse experience built with **Next.js**, **TypeScript**, **Tailwind CSS**, and the free [TMDB API](https://www.themoviedb.org/documentation/api).

## Features

- **Hero banner** with trending movie and backdrop
- **Horizontal rows** (Trending, Top Rated, Action, Comedy)
- **Responsive layout** with scrollable rows
- **Server-side data** – TMDB API key stays on the server
- **Organized code** – `components/`, `lib/`, `types/`, clear separation of concerns

## Setup

1. **Clone and install**

```bash
   cd Netflix-Clone
npm install
```

2. **TMDB API key (free)**

   - Go to [themoviedb.org](https://www.themoviedb.org) and create an account
   - Open [API Settings](https://www.themoviedb.org/settings/api) and request an API key (choose "Developer")
   - Copy the **API Key (v3 auth)**

3. **Environment**

   ```bash
   cp .env.example .env.local
   ```
   (On Windows PowerShell: `Copy-Item .env.example .env.local`)

   Edit `.env.local` and set:

```env
   TMDB_API_KEY=your_actual_api_key
```

4. **Run**

```bash
npm run dev
```

   Open [http://localhost:3000](http://localhost:3000).

## Project structure

```
src/
├── app/              # Next.js App Router (layout, page)
├── components/       # UI: Header, Hero, Row, Thumbnail, Footer
├── lib/              # API client (tmdb), constants, utils
└── types/            # TypeScript types (TMDB responses)
```

## Scripts (what each command does)

| Command | What it does |
|--------|----------------|
| `npm install` | Reads `package.json`, downloads all dependencies (Next.js, React, Tailwind, etc.) into `node_modules`, and creates/updates `package-lock.json` so installs are reproducible. |
| `npm run dev` | Starts the **development server** (Next.js). The app is available at `http://localhost:3000`, with hot reload so code changes show up without a full refresh. |
| `npm run build` | Creates a **production build**: compiles TypeScript, bundles JS/CSS, pre-renders pages where possible. Output goes to the `.next` folder. Needs a valid `TMDB_API_KEY` for the home page to pre-render with real data; otherwise the “setup required” message is shown. |
| `npm run start` | Serves the **already-built** app from `.next` (run `npm run build` first). Used for production-style runs locally. |
| `npm run lint` | Runs **ESLint** on the codebase to report style and common errors. |
| `cp .env.example .env.local` | Copies the example env file so you have a `.env.local` to put your real `TMDB_API_KEY` in. `.env.local` is not committed (see `.gitignore`). |

## What we built (overview)

1. **Next.js app** – Single project with App Router (`src/app/`). No separate frontend/backend folders; API key is only used on the server.
2. **TMDB integration** – `src/lib/tmdb.ts` talks to the free TMDB API (trending, discover by genre). Types in `src/types/tmdb.ts` match the API responses.
3. **UI** – Header (with scroll-to-solid background), Hero (big backdrop + title/overview/buttons), horizontal **Rows** of movie thumbnails, Footer. Images from TMDB via `next/image` and `src/lib/utils.ts` (`getImageUrl`).
4. **Layout** – Fixed header, main content with top padding so it’s not hidden, footer at the bottom. Error state when the API key is missing shows a short setup message.
5. **Organisation** – Reusable components in `src/components/`, API and helpers in `src/lib/`, shared types in `src/types/`, so the code stays maintainable and easy to extend.

## Data source

Movie and TV data and images are provided by [The Movie Database (TMDB)](https://www.themoviedb.org). This project is not affiliated with Netflix or TMDB.
