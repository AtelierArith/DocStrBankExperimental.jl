```
market_status(opts::PolyOpts)
```

Get the current trading status of the exchanges and overall financial markets.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> market_status(opts)
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v1*marketstatus*now*anchor for documentation on response attributes and supported keyword arguments.
