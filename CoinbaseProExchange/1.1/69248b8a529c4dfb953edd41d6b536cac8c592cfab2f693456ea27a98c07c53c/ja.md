```
show_historical_data(pair::String, interval::Int64)
```

製品の過去のレートを取得します。

# 引数

  * `pair::String` : 通貨ペアを指定します。例えば "ETH-EUR"
  * `interval::Int64` : レートは指定された間隔に基づいてグループ化されたバケットで返されます。                      [60, 300 (デフォルト), 900, 3600, 21600, 86400] の中から選択してください。すべて秒単位です。

# 例

```julia-repl
julia> show_historical_data("ETH-EUR", 3600)
300×6 DataFrame
 Row │ time                 low      high     open     close    volume  
     │ Any                  Any      Any      Any      Any      Any     
─────┼──────────────────────────────────────────────────────────────────
   1 │ 2021-06-24T11:00:00  1619.45  1650.91  1619.45  1648.84  407.623
   2 │ 2021-06-24T12:00:00  1644.02  1665.64  1648.05  1655.5   446.389
```
