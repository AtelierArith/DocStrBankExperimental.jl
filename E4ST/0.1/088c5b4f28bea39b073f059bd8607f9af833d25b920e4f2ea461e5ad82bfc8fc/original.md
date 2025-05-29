```
append_builds!(config, data, existing_table_name, build_table_name)
```

Adds new builds from `build_table_name` to `existing_table_name`.   For each row of the build table, it may denote one or more buses to connect to via the `area` and `subarea` columns.   For any column included in the existing table but not the build table that is also included in the bus table, the value from the connected bus will be used.
