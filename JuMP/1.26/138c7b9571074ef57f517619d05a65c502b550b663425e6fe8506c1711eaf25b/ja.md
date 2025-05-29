```
get_optimizer_attribute(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    attr::Union{AbstractString,MOI.AbstractOptimizerAttribute},
)
```

ソルバー固有の属性 `attr` に関連付けられた値を返します。

`attr` が `AbstractString` の場合、これは `get_optimizer_attribute(model, MOI.RawOptimizerAttribute(name))` と同等です。

!!! compat
    このメソッドは、JuMP のすべての v1.X リリースに残りますが、将来の v2.0 リリースで削除される可能性があります。代わりに [`get_attribute`](@ref) の使用をお勧めします。


参照: [`set_optimizer_attribute`](@ref), [`set_optimizer_attributes`](@ref).

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> get_optimizer_attribute(model, MOI.Silent())
false
```
