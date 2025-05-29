```
function import_instrument_event_mappings(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, data,)
```

指定されたイベントに対するデータ収集機器のマッピングを、縦断的なREDCapプロジェクトにインポートします。

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取られます)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取られます)
  * `data`: 文字列、ファイル名、またはNamedTupleやDictなどのデータ型である可能性があります
  * `format`: `data` 入力パラメータのフォーマット: `:csv`, `:json`, または `:xml` (デフォルト)。`data` が文字列またはファイル名の場合、この値は正しいフォーマットを示す必要があります。`data` がNamedTuple、Dict、または類似の型の場合、この値はデータを内部的に渡すために使用されるフォーマットを決定します。
  * `returnFormat`: 希望する出力フォーマット: `:csv`, `:json`, または `:xml` (デフォルト)
