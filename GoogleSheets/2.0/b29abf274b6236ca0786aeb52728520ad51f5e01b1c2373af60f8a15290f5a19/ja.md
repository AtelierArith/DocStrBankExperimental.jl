```
freeze!(client::GoogleSheetsClient, sheet::Sheet, rows::Int64=0, cols::Int64=0)::Dict{Any,Any}
```

シート内の行と列を固定します。

# 引数

  * `client::GoogleSheetsClient`: クライアント
  * `sheet::Sheet`: シート
  * `rows::Int64=0`: 行数
  * `cols::Int64=0`: 列数
