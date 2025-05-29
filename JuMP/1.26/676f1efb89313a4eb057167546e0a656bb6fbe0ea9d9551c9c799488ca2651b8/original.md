```
SkewSymmetricMatrixSpace()
```

Use in the [`@variable`](@ref) macro to constrain a matrix of variables to be skew-symmetric.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, Q[1:2, 1:2] in SkewSymmetricMatrixSpace())
2×2 Matrix{AffExpr}:
 0        Q[1,2]
 -Q[1,2]  0
```
