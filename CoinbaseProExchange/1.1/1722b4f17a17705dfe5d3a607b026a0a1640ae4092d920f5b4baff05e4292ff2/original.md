```
place_market_order(side::String, pair::String, amount::IntOrFloat, amount_type::String, 
                   user_data::UserInfo)
```

Place a market order using the information provided.

# Arguments

  * `side::String` : "buy" or "sell"
  * `pair::String` : Specify currency pair, for example "ETH-EUR"
  * `amount::IntOrFloat` : Specify amount in base currency (ETH, BTC etc.) or                         quote currency (EUR, USD etc.)
  * `amount_type::String` : Select either "base" or "quote" based on the amount entered
  * `user_data::UserInfo` : API data

# Example

```julia-repl
julia> place_market_order("buy", "ETH-EUR", 15, "quote", user_data)
[ Info: Order placed
Dict{String, Any} with 14 entries:
  "created_at"      => "2021-07-04T21:54:09.895868Z"
  "stp"             => "dc"
  "product_id"      => "ETH-EUR"
  "settled"         => false
  "specified_funds" => "15"
  "status"          => "pending"
  "id"              => "d275ae2b-4f34-4ce9-98a7-1147bccf07ca"
  "executed_value"  => "0"
  "post_only"       => false
  "filled_size"     => "0"
  "side"            => "buy"
  "fill_fees"       => "0"
  "funds"           => "14.92537313"
  "type"            => "market"
```
