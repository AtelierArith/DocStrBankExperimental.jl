```julia
replace_operator!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position,
    id::Int64,
    O::GradientRobustMultiPhysics.AbstractPDEOperator;
    equation_name
)

```

Replaces the id-th operator at the sepcified position of the left-hand side of the PDEDescription with the given PDEOperator.
