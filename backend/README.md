## Backend Structure

The backend is implemented in Python using FastAPI and is responsible for
exposing a REST API, handling scheduling logic, and managing persistence
(via SQLite initially, with PostgreSQL as a possible future upgrade).

The directory structure is organized as follows:

```
backend/
├── gatorsched_api/
│ ├── init.py
│ ├── main.py # FastAPI application entry point
│ ├── api/ # API route modules (endpoints)
│ ├── core/ # Application settings, configuration, logging
│ ├── db/ # Database setup (engine, sessions, migrations later)
│ ├── models/ # SQLAlchemy ORM models
│ ├── schemas/ # Pydantic models (request/response schemas)
│ └── services/ # Scheduling logic and business rules (“engine”)
│
├── tests/ # Backend unit tests (pytest)
├── requirements.txt # Python dependencies
├── pyproject.toml # Optional project metadata / tooling config
└── README.md # Backend documentation
```

### Notes

- `main.py` is the entry point for running the FastAPI server.
- API routes should remain thin and delegate logic to `services/`.
- Scheduling logic is intentionally separated from the API layer to improve
  testability and maintainability.
- SQLite will be used during development; database abstractions live under `db/`
  to allow future migration to PostgreSQL if needed.
