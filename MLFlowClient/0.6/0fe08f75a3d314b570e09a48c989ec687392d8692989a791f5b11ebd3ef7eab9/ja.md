```
setregisteredmodeltag(instance::MLFlow, name::String, key::String, value::String)
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `name:` モデルのユニークな名前。
  * `key:` [`Tag`](@ref) の名前。
  * `value:` ログされる [`Tag`](@ref) の文字列値。

# 戻り値

成功した場合は `true`。それ以外の場合は例外を発生させます。
