```
name(model::AbstractModel)
```

`model`の[`backend`](@ref)の[`MOI.Name`](@ref)属性を返すか、空の場合はデフォルトを返します。

## 例

```jldoctest
julia> model = Model();

julia> name(model)
"A JuMP Model"
```
