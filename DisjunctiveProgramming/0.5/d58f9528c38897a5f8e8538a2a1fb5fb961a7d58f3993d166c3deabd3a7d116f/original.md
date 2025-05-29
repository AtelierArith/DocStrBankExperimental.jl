```
function JuMP.add_constraint(
    model::JuMP.GenericModel,
    c::JuMP.ScalarConstraint{_LogicalExpr, MOI.EqualTo{Bool}},
    name::String = ""
)
```

Extend `JuMP.add_constraint` to allow creating logical proposition constraints  for a [`GDPModel`](@ref) with the `@constraint` macro. Users should define  logical constraints via the syntax `@constraint(model, logical_expr := true)`.
