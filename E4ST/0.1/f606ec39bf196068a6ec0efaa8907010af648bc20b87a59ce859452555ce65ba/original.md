```
force_table_types!(df::DataFrame, name, pairs...)
```

Forces `df` to have columns associated with column=>Type `pairs`.  The table's `name` is included for descriptive errors.
