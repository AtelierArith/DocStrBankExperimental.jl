```
function JuMP.add_constraint(
    model::JuMP.GenericModel,
    c::VectorConstraint{<:F, S},
    name::String = ""
) where {F <: Vector{<:LogicalVariableRef}, S <: AbstractCardinalitySet}
```

Extend `JuMP.add_constraint` to allow creating logical cardinality constraints for a [`GDPModel`](@ref) with the `@constraint` macro.
