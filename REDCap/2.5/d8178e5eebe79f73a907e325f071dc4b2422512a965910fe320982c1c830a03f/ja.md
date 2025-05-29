```
function export_survey_link(; url=get_url(), token=get_token(), returnFormat=nothing, record=nothing, instrument=nothing, event=nothing, repeat_instance=nothing,)
```

参加者の調査返却コードをエクスポートします

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `returnFormat`: 希望する出力形式: `:csv`, `:json`, または `:xml` (デフォルト)
  * `record`: レコード名
  * `instrument`: インスツルメントの名前 (調査として有効である必要があります)
  * `event`: ユニークなイベント名 (縦断的プロジェクトのみ)
  * `repeat_instance`: イベントまたはインスツルメントの繰り返しインスタンス (デフォルトは1)
