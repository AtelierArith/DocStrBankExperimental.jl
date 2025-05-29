```
stock_financials(opts::PolyOpts, stocksTicker::AbstractString; limit=5, kwargs...)
```

Get historical financial data for a stock ticker.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.
  * stocksTicker::AbstractString - The ticker symbol of the stock/equity.
  * limit::Integer - Limit the number of results.
  * kwargs::Any: A list of additional arguments to pass to the Polygon IO API.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stock_financials(opts, "AAPL", limit=5)
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v2*reference*financials*anchor for documentation on response attributes and supported keyword arguments.
