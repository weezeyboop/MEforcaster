
# Maze Engineers — Research Trend Forecaster

A standalone, self-contained HTML dashboard for tracking PubMed publication trends and forecasting product demand across Maze Engineers' full behavioral neuroscience equipment catalogue.

---

## Overview

The Research Trend Forecaster gives the Maze Engineers team instant access to publication volume trends, AI-generated demand forecasts, and recent high-impact journal publications — all organized by product category and species. No internet connection to external APIs is required after download; all trend data and forecasts are pre-baked into the file.

---

## Features

### Trend & Forecast View
- Annual publication counts (2020–2024) sourced from PubMed, displayed as a bar chart
- Four key stats per product: 2024 paper count, 5-year growth %, year-over-year change, peak year
- AI-generated demand forecast for 2025 (High / Moderate / Low)
- Confidence score (50–99%)
- Trend classification: Rising, Stable, Declining, or Emerging
- 3 key research drivers specific to each product
- Strategic recommendation for Maze Engineers
- 3 hot research areas

### Publications View
- Up to 8 recent high-impact papers (2024–2025) per product
- Sorted by journal impact factor (highest first)
- Color-coded impact tier:
  - 🟣 Purple — IF 20+ (top tier: Nature, Cell, Science)
  - 🟢 Green — IF 10–20 (high impact)
  - 🟡 Yellow — IF 5–10 (solid journals)
  - Gray — IF below 5 or unknown
- Each paper includes: title (linked to PubMed/DOI), journal, authors, date, impact factor bar
- NEW 2025 badge for papers published this year
- Live "Search latest papers on PubMed" button for every product — always up to date

---

## Product Categories

| Category | Products |
|---|---|
| Spatial Memory | Morris Water Maze, Barnes Maze, DMP Barnes Maze, Radial Arm Maze, Y Maze, T Maze, Cheeseboard Maze, Hebb Williams Maze, Puzzle Box, Linear Track, Lashley Maze, Visual X-Maze |
| Anxiety & Fear | Elevated Plus Maze, Elevated Zero Maze, Open Field Test, Light Dark Box, Fear Conditioning, Acoustic Startle Reflex, Vogel's Conflict Test, Successive Alleys, Visual Cliff Test, MCSF Test |
| Depression | Forced Swim Test, Tail Suspension Test, Sucrose Preference Test, Learned Helplessness, Sleep Deprivation |
| Social | Sociability Chamber, Tube Dominance Test, Resident Intruder Test, Social Defeat, Chronic Social Defeat Stress, Burrowing Tube, Empathy Assay, Dig Task |
| Motor | Rotarod, Balance Beam, Skilled Forelimb Reaching, Gait Test, Horizontal Ladder, Wire Hang Test, Pole Test, Treadmill, Running Wheel, Geotaxis, Stairway Test, Grid Test, Parallel Rod Floor Test |
| Operant | 5CSRTT, Operant Chamber, Conditioned Place Preference, Self-Administration, Active Passive Avoidance, Attentional Set Shifting, Hole Board, Activity Chamber |
| Pain | Von Frey Test, Hargreave's Plantar Test, Hot Plate Test, Tail Flick Test, OroFacial Pain OPAD |
| Zebrafish | Light Dark Test, Y Maze, T Maze, Shuttle Box, Swim Tunnel, Mirror Biting, 5 Choice, Associative Learning, Place Preference |
| Drosophila | Y Maze, Gravitaxis, Olfactory Conditioning, Maze Array |

---

## Species Coverage

Each product tile displays species badges indicating which model organisms the research data covers.

| Badge | Species |
|---|---|
| 🟢 mouse | *Mus musculus* |
| 🟠 rat | *Rattus norvegicus* |
| 🔵 zebrafish | *Danio rerio* |
| 🟣 drosophila | *Drosophila melanogaster* |

---

## Running the App

Because the app fetches fonts from Google Fonts, it works best when served over HTTP rather than opened directly as a file. The simplest way is a one-line local server.

### Mac / Linux
```bash
cd ~/Downloads
python3 -m http.server 8080
```
Then open: [http://localhost:8080](http://localhost:8080)

### Windows
```cmd
cd %USERPROFILE%\Downloads
python -m http.server 8080
```
Then open: [http://localhost:8080](http://localhost:8080)

### Node.js (any platform)
```bash
npx serve .
```
Then open: [http://localhost:3000](http://localhost:3000)

---

## Hosting on GitHub Pages

To make the app accessible from any browser without running a local server:

1. Create a new GitHub repository (e.g. `maze-forecaster`)
2. Upload `maze_engineers_forecaster.html` and rename it to `index.html`
3. Go to **Settings → Pages → Source** and select the `main` branch
4. Your app will be live at `https://yourusername.github.io/maze-forecaster`

---

## Updating the Data

All trend data, forecasts, and publications are stored in the `DATA` object inside the `<script>` tag of the HTML file. Each product entry contains:

```js
'Product Name': {
  c: [2020_count, 2021_count, 2022_count, 2023_count, 2024_count],
  t: 'Rising',          // trend label
  cf: 88,               // confidence %
  d: 'High',            // demand forecast
  dr: ['driver 1', 'driver 2', 'driver 3'],
  r: 'Recommendation text for Maze Engineers.',
  a: ['hot area 1', 'hot area 2', 'hot area 3'],
  p: [                  // publications array
    {
      ti: 'Paper title',
      au: 'Authors et al.',
      j:  'Journal Name',
      y:  '2024',
      m:  'Jan',
      pm: 'PMID',       // PubMed ID (or null)
      doi: '10.xxx/yyy', // DOI (or null)
      if: 6.5,          // impact factor (or null)
      n:  false         // true = NEW 2025
    }
  ]
}
```

To add a new paper, append an entry to the `p` array of the relevant product and refresh the page.

---

## Tech Stack

- Pure HTML, CSS, JavaScript — no build tools, no dependencies, no framework
- Fonts: [IBM Plex Mono](https://fonts.google.com/specimen/IBM+Plex+Mono) + [Syne](https://fonts.google.com/specimen/Syne) via Google Fonts
- PubMed live search links via NCBI E-utilities URL format
- DOI links via `doi.org`

---

## File Structure

```
maze_engineers_forecaster.html   ← entire app in one file
README.md                        ← this file
```

---

## Maintained By

Maze Engineers — [mazeengineers.com](https://mazeengineers.com)

Data sources: PubMed / NCBI, journal impact factors from Clarivate Journal Citation Reports.  
Last data update: April 2025.
