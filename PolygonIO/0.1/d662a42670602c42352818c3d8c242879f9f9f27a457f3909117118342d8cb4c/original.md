```
ticker_details(opts::PolyOpts, stocksTicker::AbstractString)
```

Get details for a ticker symbol's company/entity. This provides a general overview of the entity with information such as name, sector, exchange, logo and similar companies.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.
  * stocksTicker::AbstractString - The ticker symbol of the stock/equity.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> ticker_details(opts, "AAPL")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v2*reference*ticker*details_anchor for documentation on response attributes and supported keyword arguments.
