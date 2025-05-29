```
set_name(model::GenericModel, name::AbstractString)
```

`model`の[`backend`](@ref)の[`MOI.Name`](@ref)属性を`name`に設定します。

## 例

```jldoctest
julia> model = Model();

julia> set_name(model, "My Model")

julia> name(model)
"My Model"
```
