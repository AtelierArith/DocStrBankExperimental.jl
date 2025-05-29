```
SymmetricMatrixShape(
    side_dimension::Int;
    needs_adjoint_dual::Bool = false,
)
```

The shape object for a symmetric square matrix of `side_dimension` rows and columns.

The vectorized form contains the entries of the upper-right triangular part of the matrix given column by column (or equivalently, the entries of the lower-left triangular part given row by row).

## `needs_adjoint_dual`

By default, the [`dual_shape`](@ref) of [`SymmetricMatrixShape`](@ref) is also [`SymmetricMatrixShape`](@ref). This is true for cases such as a `LinearAlgebra.Symmetric` matrix in [`PSDCone`](@ref).

However, JuMP also supports `LinearAlgebra.Symmetric` matrix in `Zeros`, which is interpreted as an element-wise equality constraint. By exploiting symmetry, we pass only the upper triangle of the equality constraints. This works for the primal, but it leads to a factor of 2 difference in the off-diagonal dual elements. (The dual value of the `(i, j)` element in the triangle formulation should be divided by 2 when spread across the `(i, j)` and `(j, i)` elements in the square matrix formulation.) If the constraint has this dual inconsistency, set `needs_adjoint_dual = true`.
