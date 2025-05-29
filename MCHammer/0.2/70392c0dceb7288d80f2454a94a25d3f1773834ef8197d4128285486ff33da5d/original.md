Perform double exponential smoothing on the historical series.

```
es_smooth(m::DoubleES, HistoricalSeries::Vector{<:Real})
```

# Arguments

  * `m::DoubleES`: A DoubleES model with `alpha` and `beta`.
  * `HistoricalSeries`: A vector of historical data.

# Returns

A DataFrame where:

  * `level`: The smoothed level values.
  * `trend`: The estimated trend values.
  * `smoothed`: The sum of level and trend.
