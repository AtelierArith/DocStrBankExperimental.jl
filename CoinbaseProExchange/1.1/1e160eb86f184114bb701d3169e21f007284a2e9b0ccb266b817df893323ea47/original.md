```
show_product_data(pair::String, endpoint::String)
```

Fetch product data based on the selected endpoint.

# Arguments

  * `pair::String` : Specify currency pair, for example "ETH-EUR"
  * `endpoint::String` : Select one from ["24hr stats" (default), "product info", "product ticker",                                        "order book 1", "order book 2", "order book 3"]

# Example

```julia-repl
julia> show_product_data("BTC-EUR", "24hr stats")
1×6 DataFrame
 Row │ high      last      low       open      volume         volume_30day   
     │ String    String    String    String    String         String         
─────┼───────────────────────────────────────────────────────────────────────
   1 │ 29620.29  28740.89  28362.27  28642.14  1058.30490447  57346.67861744
```
