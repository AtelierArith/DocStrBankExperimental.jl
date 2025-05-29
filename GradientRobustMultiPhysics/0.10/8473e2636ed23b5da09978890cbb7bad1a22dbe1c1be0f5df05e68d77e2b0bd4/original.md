```julia
add_operator!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    equation::Int64,
    O::GradientRobustMultiPhysics.PDEOperator{T, APT<:NonlinearForm};
    equation_name
)

```

Adds the given nonlinear PDEOperator to the specified equation of the PDEDescription. Optionally, the name of the equation can be changed.
