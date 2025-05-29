```
build_constraint(_error::Function, Q::Symmetric{V, M},
                 ::PSDCone) where {V <: AbstractJuMPScalar,
                                   M <: AbstractMatrix{V}}
```

Return a `VectorConstraint` of shape [`SymmetricMatrixShape`](@ref) constraining the matrix `Q` to be positive semidefinite.

This function is used by the [`@constraint`](@ref) macros as follows:

```julia
@constraint(model, Symmetric(Q) in PSDCone())
```

The form above is usually used when the entries of `Q` are affine or quadratic expressions, but it can also be used when the entries are variables to get the reference of the semidefinite constraint, e.g.,

```julia
@variable model Q[1:2,1:2] Symmetric
# The type of `Q` is `Symmetric{VariableRef, Matrix{VariableRef}}`
var_psd = @constraint model Q in PSDCone()
# The `var_psd` variable contains a reference to the constraint
```
