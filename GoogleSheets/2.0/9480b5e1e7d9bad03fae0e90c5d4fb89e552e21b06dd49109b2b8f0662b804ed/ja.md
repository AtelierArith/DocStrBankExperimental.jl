```
append!(client::GoogleSheetsClient, sheet::Sheet, rows::Int64=0, cols::Int64=0)::Dict{Any,Any}
```

シートに行と列を追加します。

# 引数

  * `client::GoogleSheetsClient`: クライアント
  * `sheet::Sheet`: シート
  * `rows::Int64=0`: 行数
  * `cols::Int64=0`: 列数
