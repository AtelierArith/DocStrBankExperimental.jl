function import*metadata(; data, url=get*url(), token=get_token(), format=nothing, returnFormat=nothing,)

REDCapプロジェクトにメタデータ（データ辞書）をインポートします

# 名前付き引数

  * `url`: （デフォルトで `ENV["REDCAP_API_URL"]` から読み取る）
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン（デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る）
  * `data`: 文字列、ファイル名、またはNamedTupleやDictなどのデータ型である可能性があります
  * `format`: `data`入力パラメータの形式： `:csv`、 `:json`、または `:xml`（デフォルト）。 `data`が文字列またはファイル名の場合、この値は正しい形式を示す必要があります。 `data`がNamedTuple、Dict、または類似の型の場合、この値はデータを内部的に渡すために使用される形式を決定します。
  * `returnFormat`: 希望する出力形式： `:csv`、 `:json`、または `:xml`（デフォルト）
