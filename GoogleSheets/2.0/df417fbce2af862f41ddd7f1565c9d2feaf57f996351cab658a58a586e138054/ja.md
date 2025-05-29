```
format_conditional!(client::GoogleSheetsClient, range::CellIndexRange2D, format::CellFormat, 
    condition_type::ConditionType, values...)::Dict{Any,Any}
```

条件が満たされた場合にセルの範囲をフォーマットします。

# 引数

  * `client::GoogleSheetsClient`: クライアント。
  * `range::CellIndexRange2D`: セルインデックス範囲。
  * `format::CellFormat`: セルフォーマット。
  * `condition_type::ConditionType`: 条件のタイプ。
  * `values...`: 条件のための値。
