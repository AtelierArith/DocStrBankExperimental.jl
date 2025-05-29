```
show_latest_trades(pair::String)
```

Fetch list of latest trades for a given product.

# Arguments

  * `pair::String` : Specify currency pair, for example "ETH-EUR"

# Example

```julia-repl
julia> show_latest_trades("ETH-EUR")
1000×5 DataFrame
  Row │ time                      price    side    size        trade_id 
      │ Any                       Float64  String  Float64     Int64    
──────┼─────────────────────────────────────────────────────────────────
    1 │ 2021-07-06T22:23:54.963Z  1949.03  sell    0.101       22822595
    2 │ 2021-07-06T22:23:53.612Z  1948.85  sell    0.0187214   22822594
```
