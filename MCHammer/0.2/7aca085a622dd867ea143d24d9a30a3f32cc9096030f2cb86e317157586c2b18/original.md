Produce a forecast using double exponential smoothing.

```
es_forecast(m::DoubleES, HistoricalSeries::Vector{<:Real}, periods::Int)
```

# Arguments

  * `m::DoubleES`: A DoubleES model with `alpha` and `beta`.
  * `HistoricalSeries`: A vector of historical data.
  * `periods`: Number of periods to forecast beyond the historical data.

# Returns

A DataFrame with columns: `Historical`, `Level`, and `Forecast`.
