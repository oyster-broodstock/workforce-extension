# data/

> **MOCK DATA.** Every file in this directory is synthetic, generated on 2026-11-11 to exercise the folder layout,
> file naming and validator before real Cycle 1 data exist. Values are plausible but meaningless. Do not analyze or cite.
> Replace (do not edit) these files when real submissions arrive; rows carry `notes = MOCK DATA` so stragglers are easy to find.

**Scope:** Extension events, trainee records and PRISM portal analytics. Adoption surveys and partner operations data are Restricted / Confidential and are never committed.

**Nodes:** UW, VIMS, TAMU, ARS. `hub/` holds cross-project metrics and placeholders for restricted tables.

## Layout

```
data/
  <NODE>/
    raw/         files exactly as submitted by the node; never edited after upload
    processed/   outputs of versioned code (record pipeline_version); regenerate, don't hand-edit
  hub/           Coordinator / cross-node tables
```

## Conventions (Oyster CAP Data Dictionary v0.1)

- File names: `{table}_{NODE}_{CYCLE}_{YYYYMMDD}_v{n}.csv` (date = submission date). A correction is a new version file, never an overwrite.
- UTF-8 CSV, one header row with the exact dictionary field names, in dictionary order.
- `NA` for not measured / not applicable; blank cells are invalid in required fields.
- Dates `YYYY-MM-DD`; manual datetimes ISO 8601 with offset; sensor datetimes UTC (`Z`).
- Records are flagged (`qc_flag`, `qartod_flag`), never deleted. A few mock rows carry flag 3/4 on purpose.
- Access tiers: only **Shared** fields belong in this repo. Restricted fields (e.g. exact `lat_dd`/`lon_dd`, `storage_location`) are left `NA` here; Confidential tables never appear.
- IDs follow the dictionary ID_Scheme (e.g. `C1-VIMS-B0007`, `C1-ARS-F031-T0458`, `VIMS-RZ-20271020-01`).

`extension_events`, `trainees` and `prism_web_metrics` are **proposed tables not yet in Data Dictionary v0.1**; add them (or revise) before v1.0.

## Inventory

| file | rows |
|---|---|
| `ARS/raw/extension_events_ARS_C1_20271015_v1.csv` | 6 |
| `ARS/raw/trainees_ARS_C1_20271015_v1.csv` | 5 |
| `TAMU/raw/extension_events_TAMU_C1_20271015_v1.csv` | 6 |
| `TAMU/raw/trainees_TAMU_C1_20271015_v1.csv` | 3 |
| `UW/raw/extension_events_UW_C1_20271015_v1.csv` | 6 |
| `UW/raw/trainees_UW_C1_20271015_v1.csv` | 4 |
| `VIMS/raw/extension_events_VIMS_C1_20271015_v1.csv` | 6 |
| `VIMS/raw/trainees_VIMS_C1_20271015_v1.csv` | 5 |
| `hub/prism_metrics/prism_web_metrics_HUB_C1_20280701_v1.csv` | 12 |
