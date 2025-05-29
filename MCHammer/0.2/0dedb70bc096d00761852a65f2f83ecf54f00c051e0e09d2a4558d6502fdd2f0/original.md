Automatically fit optimal parameters for triple exponential smoothing by random trials.

```
es_fit(::Type{TripleES}, HistoricalSeries::Vector{<:Real}, season_length::Int, trials::Int)
```

# Arguments

  * `HistoricalSeries`: A vector of historical data.
  * `season_length`: Number of periods in a season.
  * `trials`: Number of random trials to perform.

# Returns

A `TripleES` instance with the best parameters (lowest forecast error).
