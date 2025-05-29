```
build_variable(_error::Function, variables, ::SkewSymmetricMatrixSpace)
```

Return a `VariablesConstrainedOnCreation` of shape [`SkewSymmetricMatrixShape`](@ref) creating variables in `MOI.Reals`, i.e. "free" variables unless they are constrained after their creation.

This function is used by the [`@variable`](@ref) macro as follows:

```julia
@variable(model, Q[1:2, 1:2] in SkewSymmetricMatrixSpace())
```
