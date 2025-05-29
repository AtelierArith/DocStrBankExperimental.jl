```
delete_sheet!(client::GoogleSheetsClient, spreadsheet::Spreadsheet, sheet_id::Int64)::Dict{Any,Any}
```

スプレッドシートからシートを削除します。

# 引数

  * `client::GoogleSheetsClient`: クライアント
  * `spreadsheet::Spreadsheet`: スプレッドシート
  * `sheet_id::Int64`: シートID
