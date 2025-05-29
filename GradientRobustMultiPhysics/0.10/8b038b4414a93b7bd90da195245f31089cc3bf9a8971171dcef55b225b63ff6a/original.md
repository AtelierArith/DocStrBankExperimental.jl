```julia
PDEDescription(
    name::String,
    nunknowns::Int64;
    algebraic,
    variables,
    unknown_names,
    equation_names
) -> GradientRobustMultiPhysics.PDEDescription

```

Create empty PDEDescription for a specified number of unknowns.
