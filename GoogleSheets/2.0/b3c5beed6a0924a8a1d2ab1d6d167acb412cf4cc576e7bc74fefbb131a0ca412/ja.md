```
add_sheet!(client::GoogleSheetsClient, spreadsheet::Spreadsheet, title::AbstractString)::Dict{Any,Any}
```

スプレッドシートに新しいシートを追加します。

# 引数

  * `client::GoogleSheetsClient`: クライアント
  * `spreadsheet::Spreadsheet`: スプレッドシート
  * `title::AbstractString`: シートタイトル
