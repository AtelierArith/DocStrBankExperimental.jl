```
tt_load(year::Integer, week::Integer; use_cache=true)
```

Load TidyTuesday datasets for a specific year and week. Returns a NamedTuple of DataFrames.

# Arguments

  * `year`: The year (e.g., 2024)
  * `week`: The week number (1-52)
  * `use_cache`: Whether to use cached data if available (default: true)

# Returns

A NamedTuple where each field is a DataFrame containing the dataset.
