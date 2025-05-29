```
stocks_last_trade_symbol(opts::PolyOpts, stocksTicker::AbstractString)
```

Get the most recent trade for a given stock.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * stocksTicker::AbstractString: The ticker symbol of the stock/equity.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_last_trade_symbol(opts, "AAPL")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*last_trade**stocksTicker**anchor for documentation on response attributes and supported keyword arguments.
