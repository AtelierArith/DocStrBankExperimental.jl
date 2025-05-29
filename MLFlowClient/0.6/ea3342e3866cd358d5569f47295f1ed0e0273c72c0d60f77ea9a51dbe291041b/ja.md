```
updateregisteredmodelpermission(instance::MLFlow, name::String, username::String,
    permission::Permission)
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `name:` [`RegisteredModel`](@ref) 名称。
  * `username:` [`User`](@ref) ユーザー名。
  * `permission:` 新しい [`Permission`](@ref) を付与します。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
