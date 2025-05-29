```
deletemodelversion(instance::MLFlow, name::String, version::String)
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `name:` [`RegisteredModel`](@ref) の名前。
  * `version:` [`ModelVersion`](@ref) 番号。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
