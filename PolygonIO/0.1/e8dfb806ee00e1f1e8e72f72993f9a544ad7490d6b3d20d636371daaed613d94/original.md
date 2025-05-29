```
historic_forex_ticks(opts::PolyOpts, from="AUD", to="USD", date="2020-10-14"; limit=100, kwargs...)
```

Get historic ticks for a forex currency pair.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * from: The "from" symbol of the currency pair. Example: For USD/JPY the from would be USD.
  * to: The "to" symbol of the currency pair. Example: For USD/JPY the to would be JPY.
  * date: The date/day of the historic ticks to retrieve.
  * limit: TLimit the size of the response, max 10000. Defualt 100.
  * kwargs: Additional parameters to pass to the Poly API.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> historic_forex_ticks(opts, "AUD", "AUD", "2020-10-14")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v1*historic_forex**from___to___date**anchor for documentation on response attributes and supported keyword arguments.
