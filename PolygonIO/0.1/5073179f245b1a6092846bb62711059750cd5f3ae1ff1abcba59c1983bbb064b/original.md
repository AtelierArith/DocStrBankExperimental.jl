```
stock_exchanges(opts::PolyOpts)
```

Get a list of stock exchanges which are supported by Polygon.io.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stock_exchanges(opts)
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v1*meta*exchanges*anchor for documentation on response attributes and supported keyword arguments.
