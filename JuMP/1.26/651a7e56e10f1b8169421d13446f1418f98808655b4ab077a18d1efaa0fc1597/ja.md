```
set_optimizer_attribute(
    model::Union{GenericModel,MOI.OptimizerWithAttributes},
    attr::Union{AbstractString,MOI.AbstractOptimizerAttribute},
    value,
)
```

モデルのソルバー固有の属性 `attr` を `value` に設定します。

`attr` が `AbstractString` の場合、これは `set_optimizer_attribute(model, MOI.RawOptimizerAttribute(name), value)` と同等です。

!!! compat
    このメソッドはJuMPのすべてのv1.Xリリースに残りますが、将来のv2.0リリースで削除される可能性があります。代わりに [`set_attribute`](@ref) の使用を推奨します。


参照: [`set_optimizer_attributes`](@ref), [`get_optimizer_attribute`](@ref).

## 例

```jldoctest
julia> model = Model();

julia> set_optimizer_attribute(model, MOI.Silent(), true)
```
