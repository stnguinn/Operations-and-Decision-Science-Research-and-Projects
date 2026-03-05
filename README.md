# Operations-and-Decision-Science-Research-and-Projects
Operations and Decision Science Research and Projects
# Operations and Decision Science Research and Projects

This repository contains research notes, reproducible analyses, and portfolio-ready projects focused on Operations Research (OR) and Applied Decision Science. Work products emphasize clear problem framing, measurable objectives, transparent assumptions, and end-to-end reproducibility.

## What You Will Find Here
- **Decision analysis:** problem framing, decision criteria, trade-offs, sensitivity analysis
- **Experimentation / A-B testing:** design, power, guardrails, analysis, interpretation
- **Optimization & OR methods:** linear/integer programming, network flows, scheduling, simulation (as applicable)
- **Operational analytics:** forecasting, service levels, capacity, queueing-style analyses (as applicable)
- **Reproducible reporting:** documented methods, data dictionaries, and stakeholder-ready summaries

## Repository Structure
- `projects/`
  - Individual project folders (each project is self-contained with its own README)
- `notebooks/`
  - Exploratory analysis notebooks (draft work that may later become projects)
- `src/`
  - Reusable code (helpers, utilities, shared functions)
- `data/`
  - `raw/` (immutable inputs; do not edit)
  - `processed/` (cleaned, analysis-ready datasets)
  - `external/` (third-party datasets or reference extracts, if permitted)
- `docs/`
  - Documentation site content (KPI definitions, data dictionary, runbooks)
- `models/`
  - Saved model artifacts (when relevant)
- `reports/`
  - Final write-ups, figures, and exported PDFs
- `sql/`
  - SQL scripts (schema, staging, marts, queries)
- `dbt/`
  - dbt project (staging → marts, tests, documentation)
- `docker/`
  - Docker Compose and service configuration (Postgres, Metabase, etc.)

## Standard Workflow (High Level)
1. **Land data** into a controlled landing zone (raw files remain unchanged).
2. **Ingest** data into PostgreSQL using Python (pandas + openpyxl + psycopg/sqlalchemy).
3. **Transform/model** with dbt (staging → marts) and run data quality tests.
4. **Analyze and report** using notebooks and/or SQL.
5. **Publish dashboards** (Metabase) and **maintain documentation** (MkDocs).

## How to Run (Local)
### Prerequisites
- Docker + Docker Compose
- Python 3.11+ (if running jobs outside containers)

### Quick Start
1. Clone the repo:
   - `git clone <this-repo-url>`
2. Start services:
   - `docker compose up -d`
3. Load or place input files:
   - Place files into `data/raw/` (or your configured landing directory)
4. Run ingestion:
   - `python src/ingest/run_ingest.py` (example path; adjust to your project layout)
5. Run dbt:
   - `dbt run`
   - `dbt test`
6. Open Metabase:
   - Visit the Metabase container URL shown by Docker (typically `http://localhost:3000`)

## Project Template (Per Project Folder)
Each project under `projects/<project_name>/` should include:
- `README.md` (problem statement, data, approach, results)
- `data/` (or references to shared `data/`)
- `notebooks/` or `src/`
- `outputs/` (figures, tables, final report)
- `assumptions.md` (explicit assumptions and limitations)

## Conventions
- Raw data is **immutable** once ingested.
- Every metric has a definition (see `docs/`).
- Analyses should be reproducible from a clean environment.
- Prefer clear naming and traceable transformations.

## License
Choose a license appropriate to your intended use (e.g., MIT for open sharing). If datasets are third-party, follow their terms and avoid committing restricted data.

## Contact
For questions or collaboration requests, use GitHub Issues in this repository.
