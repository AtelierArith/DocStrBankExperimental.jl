```
last_quote_currency_pair(opts::PolyOpts, from="AUD", to="USD")
```

Get the last quote tick for a forex currency pair.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * from: The "from" symbol of the pair.
  * to: The "to" symbol of the pair.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> last_quote_currency_pair(opts, "AUD", "USD")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v1*last*quote*currencies**from___to**anchor for documentation on response attributes and supported keyword arguments.
