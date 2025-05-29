```
tt_load(date::Union{String,Date}; use_cache=true)
```

Load TidyTuesday datasets for a specific date. Returns a NamedTuple of DataFrames.

# Arguments

  * `date`: Either a date string in "YYYY-MM-DD" format or a Date object
  * `use_cache`: Whether to use cached data if available (default: true)

# Returns

A NamedTuple where each field is a DataFrame containing the dataset.
