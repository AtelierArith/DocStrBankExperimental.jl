```
function export_reports(; url=get_url(), token=get_token(), report_id, format=nothing, returnFormat=nothing, fields=nothing, rawOrLabel=nothing, rawOrLabelHeaders=nothing, exportCheckboxLabel=nothing, csvDelimiter=nothing, decimalCharacter=nothing,)
```

REDCapプロジェクトのレポートデータセットをエクスポートする

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `report_id`: レポートID番号
  * `format`: 希望する出力形式: `:csv`, `:json`, `:xml` (デフォルト), または `:odm`
  * `rawOrLabel`: `:raw` (デフォルト、コーディングされた生の値をエクスポート) または `:label` (ラベルをエクスポート)
  * `rawOrLabelHeaders`: (`:flat`タイプ、`:csv`形式のみ) 生またはラベルのCSVヘッダー
  * `exportCheckboxLabel`: チェックボックスフィールド値の形式を切り替える (デフォルトはfalse)
  * `csvDelimiter`: ',' (デフォルト)、'tab'、';'、'|'、または '^'
  * `decimalCharacter`: ',' または '.' 形式を強制 (デフォルトは空)
