```julia
add_operator!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position::Vector{Int64},
    O::GradientRobustMultiPhysics.PDEOperator;
    equation_name
) -> Union{Nothing, Int64}

```

Adds the given linear PDEOperator to the left-hand side of the PDEDescription at the specified position. Optionally, the name of the equation can be changed. The id of the operator in the coressponding LHS block of PDEDescription is returned.
