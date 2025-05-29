```julia
add_operator!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position,
    O::GradientRobustMultiPhysics.AbstractPDEOperator;
    equation_name
) -> Tuple{Int64, Int64}

```

Adds the given abstract PDEOperator to the left-hand side of the PDEDescription at the specified position. The id of the operator in the coressponding LHS block of PDEDescription is returned.
