```
IDFdata(df::DataFrame, year_id::String, duration::Dict{String, T} where T<:Real)
```

Construct a IDFdata structure from a DataFrame.

### Details

  * `year_id`: string indicating the year column
  * `duration`: Dictionary mapping the dataframe id to duration.

See the tutorial for an example.
