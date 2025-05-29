```
stocks_daily_open_close(opts::PolyOpts, stocksTicker::AbstractString, date::AbstractString; adjusted=true)
```

Get the open, close and afterhours prices of a stock symbol on a certain date.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * stocksTicker::AbstractString: The ticker symbol of the stock/equity.
  * date::AbstractString: The date of the requested open/close in the format YYYY-MM-DD.
  * adjusted::Bool: Whether or not the results are adjusted for splits. By default, results are adjusted.  Set this to false to get results that are NOT adjusted for splits.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_daily_open_close(opts, "AAPL", "2017-01-01")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v1*open-close**stocksTicker___date**anchor for documentation on response attributes and supported keyword arguments.
