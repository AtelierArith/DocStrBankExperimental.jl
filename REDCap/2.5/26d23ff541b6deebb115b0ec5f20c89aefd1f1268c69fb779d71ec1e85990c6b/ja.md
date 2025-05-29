```
function export_metadata(; url=get_url(), token=get_token(), format=nothing, fields=nothing, forms=nothing,)
```

REDCapプロジェクトからメタデータ（データ辞書）をエクスポートする

# 名前付き引数

  * `url`: （デフォルトで `ENV["REDCAP_API_URL"]` から読み取る）
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン（デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る）
  * `format`: 希望する出力形式： `:csv`、 `:json`、または `:xml`（デフォルト）
  * `fields`: フィールド名（スカラーまたはベクター可）。デフォルトでは、すべてのフィールドが取得されます。
  * `fields`: データ収集機器のユニークなフォーム名（スカラーまたはベクター可）。デフォルトでは、すべてのフィールドが取得されます。
