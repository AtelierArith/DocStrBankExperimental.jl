```
ticker_types(opts::PolyOpts)
```

Get a mapping of ticker types to their descriptive names.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> ticker_types(opts)
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v2*reference*types*anchor for documentation on response attributes and supported keyword arguments.
