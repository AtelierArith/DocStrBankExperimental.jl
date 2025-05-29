```
build_variable(_error::Function, variables, ::PSDCone)
```

Return a `VariablesConstrainedOnCreation` of shape [`SymmetricMatrixShape`](@ref) constraining the variables to be positive semidefinite.

This function is used by the [`@variable`](@ref) macro as follows:

```julia
@variable(model, Q[1:2, 1:2], PSD)
```
