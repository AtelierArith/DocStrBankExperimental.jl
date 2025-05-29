```
delete_sheet!(client::GoogleSheetsClient, spreadsheet::Spreadsheet, title::AbstractString)::Dict{Any,Any}
```

スプレッドシートからシートを削除します。

# 引数

  * `client::GoogleSheetsClient`: クライアント
  * `spreadsheet::Spreadsheet`: スプレッドシート
  * `title::AbstractString`: シートタイトル
