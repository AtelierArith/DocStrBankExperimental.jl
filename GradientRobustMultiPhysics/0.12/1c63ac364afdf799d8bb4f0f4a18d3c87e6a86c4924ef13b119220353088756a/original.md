```julia
replace_rhsdata!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position::Int64,
    id::Int64,
    O::GradientRobustMultiPhysics.AbstractPDEOperator
)

```

Replaces the operator at position[id] of the right-hand side of the PDEDescription with the given PDEOperator.
