```
stock_dividends(opts::PolyOpts, stocksTicker::AbstractString)
```

Get a list of historical dividends for a stock, including the relevant dates and the amount of the dividend.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.
  * stocksTicker::AbstractString - The ticker symbol of the stock/equity.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stock_dividends(opts, "AAPL")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v2*reference_dividends**stocksTicker**anchor for documentation on response attributes and supported keyword arguments.
