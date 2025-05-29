```
stocks_snapshot_all_tickers(opts::PolyOpts, tickers::AbstractString)
```

Get the current minute, day, and previous day’s aggregate, as well as the last trade and quote for all traded stock symbols. Note: Snapshot data is cleared at 12am EST and gets populated as data is received from the exchanges. This can happen as early as 4am EST.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * tickers::AbstractString: A comma separated list of tickers to get snapshots for.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_snapshot(opts, "AAPL")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*snapshot*locale*us*markets*stocks*tickers*anchor for documentation on response attributes and supported keyword arguments.
