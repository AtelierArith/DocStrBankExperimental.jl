```
show_product_data(pair::String, endpoint::String)
```

選択したエンドポイントに基づいて製品データを取得します。

# 引数

  * `pair::String` : 通貨ペアを指定します。例えば "ETH-EUR"
  * `endpoint::String` : ["24時間統計" (デフォルト), "製品情報", "製品ティッカー", "オーダーブック 1", "オーダーブック 2", "オーダーブック 3"] の中から選択します。

# 例

```julia-repl
julia> show_product_data("BTC-EUR", "24hr stats")
1×6 DataFrame
 Row │ high      last      low       open      volume         volume_30day   
     │ String    String    String    String    String         String         
─────┼───────────────────────────────────────────────────────────────────────
   1 │ 29620.29  28740.89  28362.27  28642.14  1058.30490447  57346.67861744
```
