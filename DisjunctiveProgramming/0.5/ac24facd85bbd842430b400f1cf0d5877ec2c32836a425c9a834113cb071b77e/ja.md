```
function JuMP.add_constraint(
    model::JuMP.GenericModel,
    c::VectorConstraint{<:F, S},
    name::String = ""
) where {F <: Vector{<:LogicalVariableRef}, S <: AbstractCardinalitySet}
```

`JuMP.add_constraint`を拡張して、`@constraint`マクロを使用して[`GDPModel`](@ref)の論理基数制約を作成できるようにします。
