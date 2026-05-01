# IEG Group 1 — Integrated Energy Grids Course Project
## DTU Course 46770 | February–May 2026

---

## Repository Structure

```
IEG_Group1/
├── IEG_Group1_G.ipynb
│
├── ConsumptionCoverageNationalDecl.csv
├── costs_2025.csv
├── electricity_demand.csv
├── GUI_TOTAL_LOAD_DAYAHEAD_202312312300-202412312300.csv
├── GUI_TOTAL_LOAD_DAYAHEAD_202312312300-202412312300 (1).csv
├── GUI_TOTAL_LOAD_DAYAHEAD_202312312300-202412312300 (2).csv
│
├── ninja-pv-country-DK-nuts2-merra2.csv
├── ninja-pv-country-NO-national-merra2.csv
├── ninja-pv-country-SE-national-merra2.csv
├── ninja-pv-country-FI-national-merra2.csv
├── ninja-wind-country-DK-current_offshore-merra2.csv
├── ninja-wind-country-NO-current_offshore-merra2.csv
├── ninja-wind-country-NO-current_onshore-merra2.csv
├── ninja-wind-country-SE-current_offshore-merra2.csv
├── ninja-wind-country-SE-current_onshore-merra2.csv
├── ninja-wind-country-FI-current_offshore-merra2.csv
├── ninja-wind-country-FI-current_onshore-merra2.csv
│
├── results_task_A.nc
├── results_task_C.nc
├── results_task_G.nc
│
├── i/
│   ├── DK2ambientT.csv
│   ├── NOambientT.csv
│   ├── SEambientT.csv
│   ├── FIambientT.csv
│   └── annualheatdemandgwh.csv
│
└── README.md
```

---

## Input Files per Task

| Task | Files required |
|------|---------------|
| a | `ConsumptionCoverageNationalDecl.csv`, `costs_2025.csv`, `ninja-wind-country-DK-current_offshore-merra2.csv`, `ninja-pv-country-DK-nuts2-merra2.csv` |
| b | Same as Task a + `ninja-wind-country-DK-current_offshore-merra2.csv`, `ninja-pv-country-DK-nuts2-merra2.csv` (all weather years 1980–2024) |
| c | No new files — continues from Task a network in memory |
| d | `electricity_demand.csv`, `GUI_TOTAL_LOAD_DAYAHEAD_*.csv` (×3), all NO/SE/FI ninja files |
| f | `results_task_C.nc`, `costs_2025.csv` |
| g | `results_task_C.nc`, `costs_2025.csv`, all NO/SE/FI ninja files, `GUI_TOTAL_LOAD_DAYAHEAD_*.csv` (×3) |
| h | `results_task_G.nc`, `costs_2025.csv` |
| i | `results_task_G.nc`, `costs_2025.csv`, `i/DK2ambientT.csv`, `i/NOambientT.csv`, `i/SEambientT.csv`, `i/FIambientT.csv`, `i/annualheatdemandgwh.csv` |
| j | `results_task_G.nc`, `costs_2025.csv`, all `i/` files |

---

## Saved Network Files

The notebook saves PyPSA network states to `.nc` files at key points. These are required to run later tasks without re-running the full optimisation chain from scratch.

| File | Saved at end of | Required by |
|------|----------------|-------------|
| `results_task_A.nc` | Task a | Reference only |
| `results_task_C.nc` | Task c | Tasks f, g |
| `results_task_G.nc` | Task g | Tasks h, i, j |

**Important:** if the `.nc` files are not present, the affected tasks must be re-run in order from the beginning of the notebook. Each solve takes approximately 1–3 minutes on a standard laptop. Tasks h, i and j each load `results_task_G.nc` as a fresh network copy per iteration to avoid PyPSA internal state corruption after repeated solves.

---

## Data Sources

| Data | Source |
|------|--------|
| DK2 electricity demand | Energinet ConsumptionCoverage 2024 |
| NO, SE, FI electricity demand | ENTSO-E Transparency Platform |
| Wind and solar capacity factors | Renewables.ninja (MERRA-2 reanalysis) |
| Technology costs | PyPSA technology-data 2025 |
| Ambient temperatures (Task i) | ERA5 reanalysis (Copernicus) |
| Annual heat demand (Task i) | Eurostat energy balances |
| 1990 CO₂ baselines (Task h) | UNFCCC national inventory reports |
| EU ETS carbon price (Task h) | Ember carbon price tracker |

---

## Group 1 — DTU Course 46770
*Integrated Energy Grids, Spring 2026*

## Authors

Alison Mishel Guaman Paguay - s250330

Sofia Nuvoloni - s253195

Konstantinos Christodoulou - s253236

Vasiliki Tatouli - s253244
