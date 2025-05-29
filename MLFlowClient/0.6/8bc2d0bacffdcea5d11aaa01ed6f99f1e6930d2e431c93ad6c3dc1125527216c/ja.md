```
getlatestmodelversions(instance::MLFlow, name::String;
    stages::Array{String}=String[])
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `stages:` ステージのリスト。

# 戻り値

各リクエストステージの最新の [`ModelVersion`](@ref)。
