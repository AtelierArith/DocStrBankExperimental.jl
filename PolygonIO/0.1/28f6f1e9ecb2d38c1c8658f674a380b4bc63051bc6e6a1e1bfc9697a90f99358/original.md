```
market_holidays(opts::PolyOpts)
```

Get upcoming market holidays and their open/close times.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> market_holidays(opts)
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v1*marketstatus*upcoming*anchor for documentation on response attributes and supported keyword arguments.
