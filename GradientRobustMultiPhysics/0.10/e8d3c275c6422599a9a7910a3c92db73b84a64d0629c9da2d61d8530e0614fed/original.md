```julia
add_rhsdata!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position::Int64,
    O::GradientRobustMultiPhysics.AbstractPDEOperator
) -> Int64

```

Adds the given PDEOperator to the right-hand side of the PDEDescription at the specified position. The id of the operator in the coressponding RHS block of PDEDescription is returned.
