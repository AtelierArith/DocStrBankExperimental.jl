```
forex_previous_close(opts::PolyOpts, forexTicker="C:EURUSD"; adjusted=true)
```

Get the previous day's open, high, low, and close (OHLC) for the specified forex pair.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * forexTicker: The ticker symbol of the currency pair.
  * adjusted: Whether or not the results are adjusted for splits.  By default, results are adjusted. Set this to false to get results that are NOT adjusted for splits.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> forex_previous_close(opts, "C:EURUSD")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*aggs*ticker**forexTicker**prev*anchor for documentation on response attributes and supported keyword arguments.
