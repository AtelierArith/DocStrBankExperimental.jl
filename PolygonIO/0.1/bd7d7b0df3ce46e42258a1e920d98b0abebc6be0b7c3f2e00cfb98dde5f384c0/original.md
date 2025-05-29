```
markets(opts::PolyOpts)
```

Get a list of markets that are currently supported by Polygon.io.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> markets(opts)
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v2*reference*markets*anchor for documentation on response attributes and supported keyword arguments.
