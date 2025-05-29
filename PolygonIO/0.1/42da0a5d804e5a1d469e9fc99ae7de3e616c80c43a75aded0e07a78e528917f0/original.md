```
historic_crypto_trades(opts::PolyOpts, from="BTC", to="USD", date="2020-10-14"; limit=100, kwargs...)
```

Get historic trade ticks for a cryptocurrency pair.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * from: The "from" symbol of the crypto pair.
  * to: The "to" symbol of the crypto pair.
  * date: The date/day of the historic ticks to retrieve.
  * limit: Limit the size of the response, max 10000. Defaults to 100.
  * kwargs: Additional arguments to pass to the request.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> historic_crypto_trades(opts, "BTC", "USD", "2020-10-14")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v1*historic_crypto**from___to___date**anchor for documentation on response attributes and supported keyword arguments.
