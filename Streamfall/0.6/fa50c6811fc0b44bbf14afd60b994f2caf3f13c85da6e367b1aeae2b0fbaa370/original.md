```
extract_flow(
    data::DataFrame, gauge_id::String; suffix::String="_Q"
)::DataFrame
```

Extract streamflow data from file.

Streamflow (Q) column is identified the Gauge ID.

Flow data is identified with the suffix `_Q` by default e.g., ("000001_Q")

# Arguments

  * `data` : Observation data
  * `gauge_id` : Gauge/Node ID
  * `suffix` : Suffix used to indicate flow data (default: "_Q")

# Returns

DataFrame of observations for selected gauge.
