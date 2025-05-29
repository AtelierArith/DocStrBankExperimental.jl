```
JuMP.add_constraint(
    model::JuMP.AbstractModel,
    con::_DisjunctConstraint,
    name::String = ""
)::DisjunctConstraintRef
```

`JuMP.add_constraint`を拡張して、[`GDPModel`](@ref)に[`Disjunct`](@ref)を追加します。制約は`GDPModel`の`.ext`辞書内の`GDPData`に追加されます。
