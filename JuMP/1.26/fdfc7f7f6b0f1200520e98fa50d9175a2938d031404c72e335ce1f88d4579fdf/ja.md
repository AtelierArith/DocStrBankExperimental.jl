```
set_silent(model::GenericModel)
```

冗長性を制御する他の属性よりも優先され、ソルバーが出力を生成しないことを要求します。

参照: [`unset_silent`](@ref).

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> set_silent(model)

julia> get_attribute(model, MOI.Silent())
true

julia> unset_silent(model)

julia> get_attribute(model, MOI.Silent())
false
```
