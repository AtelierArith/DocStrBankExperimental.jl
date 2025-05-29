```
updateuseradmin(instance::MLFlow, username::String, is_admin::Bool)
```

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `username`: ユーザー名。
  * `is_admin`: 新しい管理者ステータス。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
