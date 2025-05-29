```
deleteregisteredmodeltag(instance::MLFlow, name::String, key::String)
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `name:` タグが記録された [`RegisteredModel`](@ref) の名前。
  * `key:` [`Tag`](@ref) の名前。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
