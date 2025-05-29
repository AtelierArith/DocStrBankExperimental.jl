```
setruntag(instance::MLFlow, run_id::String, key::String, value::String)
setruntag(instance::MLFlow, run::Run, key::String, value::String)
setruntag(instance::MLFlow, run::Run, tag::Tag)
```

[`Run`](@ref)に[`Tag`](@ref)を設定します。

# 引数

  * `instance`: [`MLFlow`](@ref)の設定。
  * `run_id`: [`Tag`](@ref)をログする[`Run`](@ref)のID。
  * `key`: [`Tag`](@ref)の名前。
  * `value`: ログされる[`Tag`](@ref)の文字列値。

# 戻り値

成功した場合は`true`。そうでない場合は例外を発生させます。
