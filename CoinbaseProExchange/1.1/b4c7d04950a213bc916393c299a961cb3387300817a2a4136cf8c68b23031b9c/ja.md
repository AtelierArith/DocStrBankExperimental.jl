```
show_latest_trades(pair::String)
```

指定された商品の最新の取引リストを取得します。

# 引数

  * `pair::String` : 通貨ペアを指定します。例えば "ETH-EUR"

# 例

```julia-repl
julia> show_latest_trades("ETH-EUR")
1000×5 DataFrame
  Row │ time                      price    side    size        trade_id 
      │ Any                       Float64  String  Float64     Int64    
──────┼─────────────────────────────────────────────────────────────────
    1 │ 2021-07-06T22:23:54.963Z  1949.03  sell    0.101       22822595
    2 │ 2021-07-06T22:23:53.612Z  1948.85  sell    0.0187214   22822594
```
