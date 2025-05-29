```
show_historical_data(pair::String, interval::Int64)
```

Fetch historic rates for a product.

# Arguments

  * `pair::String` : Specify currency pair, for example "ETH-EUR"
  * `interval::Int64` : Rates are returned in grouped buckets based on specified interval.                      Choose one from [60, 300 (default), 900, 3600, 21600, 86400], all in seconds.

# Example

```julia-repl
julia> show_historical_data("ETH-EUR", 3600)
300×6 DataFrame
 Row │ time                 low      high     open     close    volume  
     │ Any                  Any      Any      Any      Any      Any     
─────┼──────────────────────────────────────────────────────────────────
   1 │ 2021-06-24T11:00:00  1619.45  1650.91  1619.45  1648.84  407.623
   2 │ 2021-06-24T12:00:00  1644.02  1665.64  1648.05  1655.5   446.389
```
