```
place_limit_order(side::String, pair::String, amount::IntOrFloat, price::IntOrFloat, 
                  user_data::UserInfo)
```

提供された情報を使用してリミットオーダーを出します。

# 引数

  * `side::String` : "buy" または "sell"
  * `pair::String` : 通貨ペアを指定します。例えば "ETH-EUR"
  * `amount::IntOrFloat` : 基軸通貨（ETH、BTCなど）での金額を指定します。
  * `user_data::UserInfo` : APIデータ

# 例

```julia-repl
julia> place_limit_order("sell", "BTC-EUR", 0.0005, 30000, user_data)
[ Info: Order placed
Dict{String, Any} with 15 entries:
  "created_at"     => "2021-07-04T21:59:11.083132Z"
  "price"          => "30000"
  "stp"            => "dc"
  "product_id"     => "BTC-EUR"
  "settled"        => false
  "status"         => "pending"
  "id"             => "cae9158e-1660-448e-bd9a-d368ce3fdc8a"
  "executed_value" => "0"
  "post_only"      => false
  "size"           => "0.0005"
  "filled_size"    => "0"
  "side"           => "sell"
  "time_in_force"  => "GTC"
  "fill_fees"      => "0"
  "type"           => "limit"
```
