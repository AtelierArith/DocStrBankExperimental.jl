Perform simple exponential smoothing on the historical series.

```
es_smooth(m::SimpleES, HistoricalSeries::Vector{<:Real}; forecast_only::Bool=false)
```

# Arguments

  * `m::SimpleES`: A SimpleES model containing the smoothing constant `alpha`.
  * `HistoricalSeries`: A vector of historical data.
  * `forecast_only` (optional): If true, only the smoothed forecast is returned.

# Returns

A dataframe of smoothed values or the original and smoothed values.
