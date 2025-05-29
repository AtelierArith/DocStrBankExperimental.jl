```
forex_snapshot_all_tickers(opts::PolyOpts; kwargs...)
```

Get the current minute, day, and previous day’s aggregate, as well as the last trade and quote for all traded forex symbols. Note: Snapshot data is cleared at 12am EST and gets populated as data is received from the exchanges. This can happen as early as 4am EST.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * kwargs: The keyword arguments to pass to the PolyOpts.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> forex_snapshot_all_tickers(opts)
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*snapshot*locale*global*markets*forex*tickers*anchor for documentation on response attributes and supported keyword arguments.
