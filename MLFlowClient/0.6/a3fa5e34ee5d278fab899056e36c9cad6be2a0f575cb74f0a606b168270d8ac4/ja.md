```
updatemodelversion(instance::MLFlow, name::String, version::String;
    description::Union{String, Missing}=missing)
```

# 引数

  * `instance:` [`MLFlow`](@ref) 設定。
  * `name:` [`RegisteredModel`](@ref) の名前。
  * `version:` [`ModelVersion`](@ref) 番号。
  * `description:` [`ModelVersion`](@ref) のオプションの説明。

# 戻り値

このモデルのレジストリに生成された [`ModelVersion`](@ref)。
