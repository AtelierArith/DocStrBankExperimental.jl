```
function export_survey_queue_link(;record=nothing,returnFormat=nothing)
```

参加者の調査キューリンクをエクスポートする

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `returnFormat`: 希望する出力形式: `:csv`, `:json`, または `:xml` (デフォルト)
  * `record`: レコード名
