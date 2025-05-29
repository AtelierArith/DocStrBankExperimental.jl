```
stocks_snapshot_ticker(opts::PolyOpts, stocksTicker::AbstractString)
```

Get the current minute, day, and previous day’s aggregate, as well as the last trade and quote for a single traded stock ticker. Note: Snapshot data is cleared at 12am EST and gets populated as data is received from the exchanges. This can happen as early as 4am EST.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * stocksTicker::AbstractString: The ticker symbol of the stock/equity.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_snapshot_ticker(opts, "AAPL")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*snapshot*locale*us*markets*stocks_tickers**stocksTicker**anchor for documentation on response attributes and supported keyword arguments.
