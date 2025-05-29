```
get(client::GoogleSheetsClient, ranges::CellRanges)::Vector{CellRangeValues}
```

スプレッドシートから複数のセル値の範囲を取得します。

# 引数

  * `client::GoogleSheetsClient`: クライアント
  * `ranges::CellRanges`: セル範囲
