```
function export_user_role_assignments(; url=get_url(), token=get_token(), format=nothing, )
```

REDCapプロジェクトから役割の割り当てをエクスポートする

# 名前付き引数

  * `url`: (デフォルトで`ENV["REDCAP_API_URL"]`から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取る)
  * `format`: 希望する出力形式: `:csv`、`:json`、または`:xml` (デフォルト)
