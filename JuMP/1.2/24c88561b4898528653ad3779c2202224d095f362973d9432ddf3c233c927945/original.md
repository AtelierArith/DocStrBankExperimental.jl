```
build_constraint(
    _error::Function,
    Q::AbstractMatrix{<:AbstractJuMPScalar},
    ::PSDCone,
)
```

Return a `VectorConstraint` of shape [`SquareMatrixShape`](@ref) constraining the matrix `Q` to be symmetric and positive semidefinite.

This function is used by the [`@constraint`](@ref) macro as follows:

```julia
@constraint(model, Q in PSDCone())
```
