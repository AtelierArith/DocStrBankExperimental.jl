```
real_time_currency_conversion(opts::PolyOpts, from="AUD", to="USD"; amount=100, precision=2)
```

Get currency conversions using the latest market conversion rates. Note than you can convert in both directions. For example USD to CAD or CAD to USD.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * from: The "from" symbol of the pair.
  * to: The "to" symbol of the pair.
  * amount: The amount to convert.
  * precision: The decimal precision of the conversion. Defaults to 2 which is 2 decimal places accuracy.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> real_time_currency_conversion(opts, "AUD", "USD"; amount=100, precision=2)
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v1*conversion**from___to**anchor for documentation on response attributes and supported keyword arguments.
