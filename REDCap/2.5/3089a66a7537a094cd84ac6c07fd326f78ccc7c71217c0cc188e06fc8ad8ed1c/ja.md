```
function delete_user_roles(; url=get_url(), token=get_token(), roles,)
```

REDCapプロジェクトからロールを削除する

# 名前付き引数

  * `url`: (デフォルトで`ENV["REDCAP_API_URL"]`から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取る)
  * `roles`: 一意のロール名 (スカラーまたはベクター可能)
