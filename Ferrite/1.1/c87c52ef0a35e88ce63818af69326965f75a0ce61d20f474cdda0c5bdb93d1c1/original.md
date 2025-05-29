```
get_rhs_data(ch::ConstraintHandler, A::SparseMatrixCSC) -> RHSData
```

Returns the needed [`RHSData`](@ref) for [`apply_rhs!`](@ref).

This must be used when the same stiffness matrix is reused for multiple steps, for example when timestepping, with different non-homogeneouos Dirichlet boundary conditions.
