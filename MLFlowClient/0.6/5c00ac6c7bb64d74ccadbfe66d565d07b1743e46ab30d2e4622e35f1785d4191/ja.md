```
restorerun(instance::MLFlow, run_id::String)
restorerun(instance::MLFlow, run::Run)
```

削除された [`Run`](@ref) を復元します。

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `run_id`: 復元する [`Run`](@ref) の ID。

# 戻り値

成功した場合は `true` を返します。それ以外の場合は例外を発生させます。
