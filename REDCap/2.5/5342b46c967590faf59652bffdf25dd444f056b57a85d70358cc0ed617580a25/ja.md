```
function export_version(; url=get_url(), token=get_token(),)
```

REDCapのバージョンをエクスポートします

# 名前付き引数

  * `url`: (デフォルトで`ENV["REDCAP_API_URL"]`から読み取ります)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取ります)
