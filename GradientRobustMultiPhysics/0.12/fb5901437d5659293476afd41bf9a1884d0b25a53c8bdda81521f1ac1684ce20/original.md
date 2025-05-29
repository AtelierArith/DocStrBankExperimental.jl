```julia
add_unknown!(
    PDE::GradientRobustMultiPhysics.PDEDescription;
    equation_name,
    unknown_name,
    variables,
    algebraic_constraint
) -> Int64

```

Adds another unknown to the PDEDescription. With the optional argument algebraic_constraint = true the unknown and the related equation can be mask as an algebraic constraint. (Currently this only has a consequence if the system is integrated in time with the Crank-Nicolson rule.)
