```
stocks_previous_close(opts::PolyOpts, stocksTicker::AbstractString; adjusted=true)
```

Get the previous day's open, high, low, and close (OHLC) for the specified stock ticker.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * stocksTicker::AbstractString: The ticker symbol of the stock/equity.
  * adjusted::Bool: Whether or not the results are adjusted for splits.  By default, results are adjusted. Set this to false to get results that are NOT adjusted for splits.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_previous_close(opts, "AAPL")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*aggs*ticker**stocksTicker**prev*anchor for documentation on response attributes and supported keyword arguments.
