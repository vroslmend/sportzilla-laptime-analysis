# Karting Analysis

The original Python analysis behind a collaborative karting dashboard for tracks in Lahore. This repository turns RaceFacer leaderboard snapshots into comparisons of lap-time distributions, rankings, performance tiers, gaps to the fastest driver and record progression.

[Live dashboard](https://karting-dashboard.vercel.app/) · [Current system source](https://github.com/farhanj21/karting-analysis-system)

## About the data

The CSV files contain each driver's best recorded time from public RaceFacer leaderboards. They are leaderboard snapshots, not lap-by-lap telemetry, so the analysis compares drivers' best times rather than consistency within individual sessions.

| Track | Snapshot | Rows |
| --- | --- | ---: |
| Sportzilla | 29 December 2025 | 3,589 |
| Apex Autodrome | 9 December 2025 | 1,783 |
| Sportzilla archive | 1 December 2025 | 2,136 |

## Repository structure

```text
Apex Autodrome/
  apex_autodrome_scrapper.ipynb  # RaceFacer scraper
  data_apex.csv                  # leaderboard snapshot
  race-analysis-apex.ipynb      # analysis notebook
  race-analysis-apex.html       # exported report
Sportzilla/
  sportzilla_scrapper.ipynb      # RaceFacer scraper
  data_sportzilla.csv            # leaderboard snapshot
  lap-analysis-sportzilla.ipynb  # analysis notebook
  lap-analysis-sportzilla.html   # exported report
  1st December 2025/             # earlier snapshot and report
  Documentation/                 # earlier analysis material
```

## Run locally

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
jupyter lab
```

Open the analysis notebook inside the relevant track folder. The notebooks read the CSV beside them and include their generated charts and tables in the saved output.

## Notes

- the notebooks use a 105-second cutoff to remove obvious outliers from the compared leaderboard data
- the scrapers depend on RaceFacer's current page structure and may need selector updates if that structure changes
- the included HTML reports are static exports of the saved notebook results

## Credits

I worked primarily on the initial data cleaning and statistical analysis in this repository. [Farhan](https://github.com/farhanj21) expanded the scraping and analysis work and led the later development of the current multi-track dashboard and application.
