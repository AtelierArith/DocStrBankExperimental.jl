```
crypto_snapshot_ticker_full_book(opts::PolyOpts, ticker="X:BTCUSD")
```

Get the current level 2 book of a single ticker. This is the combined book from all of the exchanges. Note: Snapshot data is cleared at 12am EST and gets populated as data is received from the exchanges.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * ticker: The cryptocurrency ticker.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> crypto_snapshot_ticker_full_book(opts, "X:BTCUSD")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v2*snapshot*locale*global*markets*crypto*tickers**ticker**book*anchor for documentation on response attributes and supported keyword arguments.
