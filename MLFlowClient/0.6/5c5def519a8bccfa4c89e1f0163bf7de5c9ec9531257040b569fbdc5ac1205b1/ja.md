```
setmodelversiontag(instance::MLFlow, name::String, key::String, value::String)
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `name:` モデルのユニークな名前。
  * `version:` モデルのバージョン番号。
  * `key:` [`Tag`](@ref) の名前。
  * `value:` ログに記録されるタグの文字列値。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
