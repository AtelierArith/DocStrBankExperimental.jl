```
function export_project_info(; url=get_url(), token=get_token(), format=nothing,)
```

REDCapプロジェクトの基本属性をエクスポートします

# 名前付き引数

  * `url`: (デフォルトで`ENV["REDCAP_API_URL"]`から読み取ります)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取ります)
  * `format`: 希望する出力形式: `:csv`、`:json`、または`:xml` (デフォルト)
