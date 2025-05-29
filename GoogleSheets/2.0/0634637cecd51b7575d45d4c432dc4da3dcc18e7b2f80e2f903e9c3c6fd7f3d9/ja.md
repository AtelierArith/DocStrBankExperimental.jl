```
batch_update!(client::GoogleSheetsClient, spreadsheet::Spreadsheet, body::Dict)::Dict{Any,Any}
```

スプレッドシートに1つ以上の更新を適用します。

各リクエストは適用される前に検証されます。リクエストのいずれかが無効な場合、全体のリクエストは失敗し、何も適用されません。

一般的なbatch_update!機能: チャート: https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets/charts フィルタ: https://developers.google.com/sheets/api/guides/filters 基本的な書式設定: https://developers.google.com/sheets/api/samples/formatting 条件付き書式設定: https://developers.google.com/sheets/api/samples/conditional-formatting 条件付き書式設定: https://developers.google.com/sheets/api/guides/conditional-format

# 引数

  * `client::GoogleSheetsClient`: クライアント
  * `spreadsheet::Spreadsheet`: スプレッドシート
  * `body::Dict`: 更新ボディ
