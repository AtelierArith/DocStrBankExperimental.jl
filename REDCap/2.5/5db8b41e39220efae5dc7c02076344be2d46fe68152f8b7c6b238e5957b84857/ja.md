```
function export_events(; url=get_url(), token=get_token(), format=nothing, arms=nothing,)
```

長期的なREDCapプロジェクトからイベントをエクスポートする

# 名前付き引数

  * `url`: (デフォルトで`ENV["REDCAP_API_URL"]`から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取る)
  * `format`: 希望する出力形式: `:csv`、`:json`、または`:xml` (デフォルト)
  * `arms`: イベントを取得する研究アーム (デフォルトですべてが含まれる)
