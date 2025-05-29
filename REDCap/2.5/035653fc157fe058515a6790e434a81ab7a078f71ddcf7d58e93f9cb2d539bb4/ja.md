```
function export_records(; url=get_url(), token=get_token(), format=nothing, type=nothing, records=nothing, fields=nothing, forms=nothing, events=nothing, rawOrLabel=nothing, rawOrLabelHeaders=nothing, exportCheckboxLabel=nothing, exportSurveyFields=nothing, exportDataAccessGroups=nothing, filterLogic=nothing, dateRangeBegin=nothing, dateRangeEnd=nothing, csvDelimiter=nothing, decimalCharacter=nothing, exportBlankForGrayFormStatus=nothing)
```

REDCapプロジェクトからレコードをエクスポートする

# 名前付き引数

  * `url`: (デフォルトで`ENV["REDCAP_API_URL"]`から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取る)
  * `format`: 希望する出力形式: `:csv`, `:json`, `:xml` (デフォルト), または `:odm`
  * `type`: `:flat` (デフォルト) または `:eav`
  * `records`: 特定のレコードにエクスポートを制限するオプション (スカラーまたはベクター可)
  * `fields`: 特定のフィールド名にエクスポートを制限するオプション (スカラーまたはベクター可)
  * `forms`: 特定のフォーム名にエクスポートを制限するオプション (スカラーまたはベクター可)
  * `events`: (縦断的プロジェクトのみ) 特定のユニークイベント名にエクスポートを制限するオプション (スカラーまたはベクター可)
  * `rawOrLabel`: `:raw` (デフォルト、コーディングされた生の値をエクスポート) または `:label` (ラベルをエクスポート)
  * `rawOrLabelHeaders`: (`:flat`タイプ、`:csv`形式のみ) 生のまたはラベルのCSVヘッダー
  * `exportCheckboxLabel`: チェックボックスフィールド値の形式を切り替える (デフォルトはfalse)
  * `exportSurveyFields`: 調査識別子およびタイムスタンプフィールドをエクスポートするオプション (デフォルトはfalse)
  * `exportDataAccessGroups`: "redcap*data*access_group"フィールドをエクスポートするオプション (デフォルトはfalse)
  * `filterLogic` : ロジック文字列に基づいてレコードをフィルタリングするオプション
  * `dateRangeBegin`: 特定の日時以降に作成または変更されたレコードに出力を制限するオプション
  * `dateRangeEnd`: 特定の日時以前に作成または変更されたレコードに出力を制限するオプション
  * `csvDelimiter`: ',' (デフォルト), 'tab', ';', '|', または '^'
  * `decimalCharacter`: ',' または '.' 形式を強制 (デフォルトは空)
  * `exportBlankForGrayFormStatus`: グレーのステータスアイコンを持つインスツルメント完了ステータスフィールドのために空の値をエクスポートするオプション
