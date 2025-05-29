```
stock_splits(opts::PolyOpts, stocksTicker::AbstractString)
```

Get a list of historical stock splits for a ticker symbol, including the execution and payment dates of the stock split, and the split ratio.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.
  * stocksTicker::AbstractString - The ticker symbol of the stock/equity.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stock_splits(opts, "AAPL")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v2*reference_splits**stocksTicker**anchor for documentation on response attributes and supported keyword arguments.
