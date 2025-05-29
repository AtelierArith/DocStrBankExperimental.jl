```
forex_snapshot_gainers_losers(opts::PolyOpts, direction="gainers")
```

Get the current top 20 gainers or losers of the day in forex markets. Top gainers are those tickers whose price has increased by the highest percentage since the previous day's close. Top losers are those tickers whose price has decreased by the highest percentage since the previous day's close. Note: Snapshot data is cleared at 12am EST and gets populated as data is received from the exchanges.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * direction: The direction of the snapshot results to return. "gainers" or "losers".

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> forex_snapshot_gainers_losers(opts, "losers")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*snapshot*locale*global*markets*forex**direction**anchor for documentation on response attributes and supported keyword arguments.
