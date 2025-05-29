```
validate_signals(signals)
```

Perform both table-level and row-level validation checks on the content of `signals`, a presumed `onda.signal` table. Returns `signals`.

This function will throw an error in any of the following cases:

  * `Legolas.validate(Tables.schema(signals), SignalV2SchemaVersion())` throws an error
  * `SignalV2(r)` errors for any `r` in `Tables.rows(signals)`
  * `signals` contains rows with duplicate `file_path`s
