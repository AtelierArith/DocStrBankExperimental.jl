```
function export_survey_participants(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, instrument=nothing, event=nothing, repeat_instance=nothing,)
```

アンケート参加者のリストをエクスポートする

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCap プロジェクトおよびユーザー名に特有の API トークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `returnFormat`: 希望する出力形式: `:csv`, `:json`, または `:xml` (デフォルト)
  * `instrument`: インスツルメントの名前 (アンケートとして有効である必要があります)
  * `event`: ユニークなイベント名 (縦断的プロジェクトのみ)
