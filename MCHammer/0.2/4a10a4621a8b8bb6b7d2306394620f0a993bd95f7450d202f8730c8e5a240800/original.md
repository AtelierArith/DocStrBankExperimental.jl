Produce a forecast using triple exponential smoothing (Holt–Winters method) with seasonal adjustment.

```
es_forecast(m::TripleES, HistoricalSeries::Vector{<:Real}, periods_out::Int; forecast_only::Bool=false)
```

# Arguments

  * `m::TripleES`: A TripleES model with `season_length`, `alpha`, `beta`, and `gamma`.
  * `HistoricalSeries`: A vector of historical data.
  * `periods_out`: Number of periods to forecast beyond the historical data.
  * `forecast_only` (optional): If true, returns only the forecasted values.

# Returns

Either a vector of forecasted values (if `forecast_only=true`) or the complete in-sample forecast.
