```
mode(model::GenericModel)
```

`model`の[`ModelMode`](@ref)を返します。

## 例

```jldoctest
julia> model = Model();

julia> mode(model)
AUTOMATIC::ModelMode = 0
```
