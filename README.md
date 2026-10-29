# SCORE BATTLE

A browser arcade game: stay fixed at the bottom, aim with the left/right arrow keys, and press Space to shoot. Hit all 10 targets and submit your score to the leaderboard.

## Files
- `index.html` — game layout
- `style.css` — responsive styling
- `game.js` — aiming, targets, shots, score and leaderboard UI
- `server.js` — Node.js web server and score API
- `package.json` — Render start command and dependencies

## Run locally
Requires Node.js 20 or newer.

```bash
npm install
npm start
```

Then open `http://localhost:3000`.

## Deploy to Render as a Web Service
1. Push these files to the `main` branch of your GitHub repository.
2. In Render, choose **New + → Web Service** and connect `ruumo-14/scorebattle-to-gun`.
3. Runtime: Node. Build command: `npm install`. Start command: `npm start`.
4. Deploy. Render provides a public URL.

## Persistent shared leaderboard (recommended)
The app supports PostgreSQL through `DATABASE_URL`. Without a database, scores are kept in server memory only; they can disappear after a restart or redeploy.

1. Create a PostgreSQL database in Render.
2. Copy its **Internal Database URL** (when the web service and database are in the same Render region).
3. Open the Web Service → **Environment** and add `DATABASE_URL` with that URL.
4. Save changes and redeploy. The server automatically creates the `scores` table.

The API validates score submissions but, like most client-side arcade games, the score is not cheat-proof. Do not use it for prizes or anything requiring verified competition.