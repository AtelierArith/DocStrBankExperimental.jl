```
HermitianMatrixShape(
    side_dimension::Int;
    needs_adjoint_dual::Bool = false,
)
```

The shape object for a Hermitian square matrix of `side_dimension` rows and columns.

The vectorized form corresponds to [`MOI.HermitianPositiveSemidefiniteConeTriangle`](@ref).

## `needs_adjoint_dual`

By default, the [`dual_shape`](@ref) of [`HermitianMatrixShape`](@ref) is also [`HermitianMatrixShape`](@ref). This is true for cases such as a `LinearAlgebra.Hermitian` matrix in [`HermitianPSDCone`](@ref).

However, JuMP also supports `LinearAlgebra.Hermitian` matrix in `Zeros`, which is interpreted as an element-wise equality constraint. By exploiting symmetry, we pass only the upper triangle of the equality constraints. This works for the primal, but it leads to a factor of 2 difference in the off-diagonal dual elements. (The dual value of the `(i, j)` element in the triangle formulation should be divided by 2 when spread across the `(i, j)` and `(j, i)` elements in the square matrix formulation.) If the constraint has this dual inconsistency, set `needs_adjoint_dual = true`.
