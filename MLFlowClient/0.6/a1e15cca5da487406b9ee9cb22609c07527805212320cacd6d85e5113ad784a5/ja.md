```
deleterun(instance::MLFlow, run_id::String)
deleterun(instance::MLFlow, run::Run)
```

[`Run`](@ref) を削除のためにマークします。

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `run_id`: 削除する [`Run`](@ref) のID。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
