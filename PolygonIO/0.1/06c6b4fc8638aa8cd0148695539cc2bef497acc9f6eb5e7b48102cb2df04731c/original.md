```
forex_grouped_daily_bars(opts::PolyOpts, date="2020-10-14"; adjusted=true)
```

Get the daily open, high, low, and close (OHLC) for the entire forex markets.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * date: The beginning date for the aggregate window.
  * adjusted: Whether or not the results are adjusted for splits.  By default, results are adjusted. Set this to false to get results that are NOT adjusted for splits.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> forex_grouped_daily_bars(opts, "2020-10-14")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*aggs*grouped*locale*global*market_fx**date**anchor for documentation on response attributes and supported keyword arguments.
