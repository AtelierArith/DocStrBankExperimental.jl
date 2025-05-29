```
condition_mappings(opts::PolyOpts, tickertype="trades")
```

Get a unified numerical mapping for conditions on trades and quotes. Each feed/exchange uses its own set of codes to identify conditions, so the same condition may have a different code depending on the originator of the data. Polygon.io defines its own mapping to allow for uniformly identifying a condition across feeds/exchanges.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.
  * tickertype::AbstractString - The type of ticks to return mappings for. Must be one of "trades" or "quotes".

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> condition_mappings(opts, "trades")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v1*condition*mappings*anchor for documentation on response attributes and supported keyword arguments.
