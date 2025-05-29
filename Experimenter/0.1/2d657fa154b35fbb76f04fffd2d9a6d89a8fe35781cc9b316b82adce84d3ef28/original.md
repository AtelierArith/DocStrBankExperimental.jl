```
export_db(db::ExperimentDatabase, outfile::AbstractString, experiment_names...)
```

Opens a new database at `outfile` and inserts experiments from `db` into the new db, where the names of the experiment are listed in the final input.
