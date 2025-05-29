```
updateregisteredmodel(instance::MLFlow, name::String;
    description::Union{String, Missing}=missing)
```

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `name`: [`RegisteredModel`](@ref) のユニークな名前識別子。
  * `description`: 提供された場合、この [`RegisteredModel`](@ref) の説明を更新します。

# 戻り値

[`RegisteredModel`](@ref) 型のインスタンス。
