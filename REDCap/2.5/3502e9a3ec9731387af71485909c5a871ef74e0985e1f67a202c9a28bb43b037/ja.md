```
function delete_users(; url=get_url(), token=get_token(), users)
```

REDCapプロジェクトからユーザーを削除します

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取られます)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取られます)
  * `users`: ユーザー名 (スカラーまたはベクター可能)
