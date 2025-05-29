```
crypto_snapshot_ticker(opts::PolyOpts, ticker="X:BTCUSD")
```

Get the current minute, day, and previous day’s aggregate, as well as the last trade and quote for a single traded cryptocurrency symbol. Note: Snapshot data is cleared at 12am EST and gets populated as data is received from the exchanges.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * ticker: Ticker of the snapshot.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> crypto_snapshot_ticker(opts, "X:BTCUSD")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v2*snapshot*locale*global*markets*crypto_tickers**ticker**anchor for documentation on response attributes and supported keyword arguments.
