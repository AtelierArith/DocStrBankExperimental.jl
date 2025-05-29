```
crypto_daily_open_close(opts::PolyOpts, from="BTC", to="USD", date="2020-10-14"; adjusted=true)
```

Get the open, close prices of a cryptocurrency symbol on a certain day.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * from: The "from" symbol of the pair.
  * to: The "to" symbol of the pair.
  * date: The date of the requested open/close in the format YYYY-MM-DD.
  * adjusted: Whether or not the results are adjusted for splits. By default, results are adjusted. Set this to false to get results that are NOT adjusted for splits.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> crypto_daily_open_close(opts, "BTC", "USD", "2020-10-14")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v1*open-close_crypto**from___to___date**anchor for documentation on response attributes and supported keyword arguments.
