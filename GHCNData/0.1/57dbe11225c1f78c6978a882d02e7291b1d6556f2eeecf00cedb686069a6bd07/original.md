```
convert_to_time_series(df::DataFrame)
```

Converts a `DataFrame` loaded via `load_data_file` from the original format, in which each row contains a month's worth of data for a particular ELEMENT (variable type e.g. precip, temperature, etc), to a format in which each row contains a single day's worth of data with for a single ELEMENT type. Only the element types already present in `df` will be included in the new `DataFrame`.
