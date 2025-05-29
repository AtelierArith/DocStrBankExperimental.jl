```
function import_records(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, type=nothing, overwriteBehavior=nothing, forceAutoNumber=nothing, backgroundProcess=nothing, data, dateFormat=nothing, csvDelimiter=nothing, returnContent=nothing,)
```

REDCapプロジェクトにレコードをインポートする

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `format`: 希望する出力形式: `:csv`, `:json`, `:xml` (デフォルト), または `:odm`
  * `type`: `:flat` (デフォルト) または `:eav`
  * `overwriteBehavior`: 空の値でデータを上書きする (デフォルトでは、これらは無視される)
  * `forceAutoNumber`: レコード番号を自動的に決定するオプション (デフォルトでは提供される必要がある)
  * `backgroundProcess`: 大きなアップロードの場合はtrueに設定
  * `data`: 文字列、ファイル名、またはNamedTupleやDictなどのデータ型である可能性があります
  * `format`: `data`入力パラメータの形式: `:csv`, `:json`, または `:xml` (デフォルト)。`data`が文字列またはファイル名の場合、この値は正しい形式を示す必要があります。`data`がNamedTuple、Dict、または類似の型の場合、この値はデータを内部的に渡すために使用される形式を決定します。
  * `returnFormat`: 希望する出力形式: `:csv`, `:json`, または `:xml` (デフォルト)
  * `dateFormat`: `:MDY`, `:DMY`, または `:YMD` (デフォルト)
  * `csvDelimiter`: ',' (デフォルト), 'tab', ';', '|', または '^'
  * `returnContent`: 戻り値を設定 (`:count` (デフォルト), `:lds`, または `:auto_lds`)
