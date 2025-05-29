```
place_market_order(side::String, pair::String, amount::IntOrFloat, amount_type::String, 
                   user_data::UserInfo)
```

提供された情報を使用してマーケットオーダーを出します。

# 引数

  * `side::String` : "buy" または "sell"
  * `pair::String` : 通貨ペアを指定します。例えば "ETH-EUR"
  * `amount::IntOrFloat` : 基軸通貨（ETH、BTCなど）または見積通貨（EUR、USDなど）での金額を指定します。
  * `amount_type::String` : 入力された金額に基づいて "base" または "quote" を選択します
  * `user_data::UserInfo` : APIデータ

# 例

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
