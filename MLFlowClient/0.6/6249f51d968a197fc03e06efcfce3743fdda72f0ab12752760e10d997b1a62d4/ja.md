```
deletemodelversiontag(instance::MLFlow, name::String, version::String, key::String)
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `name:` タグが記録された [`RegisteredModel`](@ref) の名前。
  * `version:` タグが記録された [`ModelVersion`](@ref) 番号。
  * `key:` [`Tag`](@ref) の名前。

# 戻り値

成功した場合は `true`。それ以外の場合は例外を発生させます。
