```
function import_arms(; url=get_url(), token=get_token(), format=nothing, data, returnFormat=nothing, override=nothing,)
```

REDCapプロジェクトに新しい研究アームをインポートするか、既存のアームの名前を変更します。

# 注意事項

研究アームを削除すると、含まれているレコードとデータも削除されます。

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `arms`: 研究アームの名前 (スカラーまたはベクターで指定可能)
  * `override`: trueの場合、すべての既存のアームが消去されます; falseの場合（デフォルト）、既存のアームは名前を変更することのみ可能です
  * `data`: 文字列、ファイル名、またはNamedTupleやDictなどのデータ型である可能性があります
  * `format`: `data`入力パラメータのフォーマット: `:csv`, `:json`, または `:xml`（デフォルト）。`data`が文字列またはファイル名の場合、この値は正しいフォーマットを示す必要があります。`data`がNamedTuple、Dict、または類似の型の場合、この値はデータを内部的に渡すために使用されるフォーマットを決定します。
  * `returnFormat`: 希望する出力フォーマット: `:csv`, `:json`, または `:xml`（デフォルト）
