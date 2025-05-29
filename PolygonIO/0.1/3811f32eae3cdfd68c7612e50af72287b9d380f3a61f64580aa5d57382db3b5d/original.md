```
stocks_grouped_daily_bars(opts::PolyOpts, date::AbstractString; adjusted=true)
```

Get the daily open, high, low, and close (OHLC) for the entire stocks/equities markets.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * date::AbstractString: The beginning date for the aggregate window.
  * adjusted::Bool: Whether or not the results are adjusted for splits. By default, results are adjusted.  Set this to false to get results that are NOT adjusted for splits.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_grouped_daily_bars(opts, "2017-01-01")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*aggs*grouped*locale*us*market_stocks**date**anchor for documentation on response attributes and supported keyword arguments.
