```
JuMP.add_constraint(
    model::JuMP.AbstractModel,
    con::_DisjunctConstraint,
    name::String = ""
)::DisjunctConstraintRef
```

Extend `JuMP.add_constraint` to add a [`Disjunct`](@ref) to a [`GDPModel`](@ref).  The constraint is added to the `GDPData` in the `.ext` dictionary of the `GDPModel`.
