```
get_matrix(op::AbstractOperator)
```

Returns the `Matrix` associated with operator `op`.

# Examples

```jldoctest
julia> z = sparse(sigma_z())
(2, 2)-element Snowflurry.SparseOperator:
Underlying data ComplexF64:
 1.0 + 0.0im        ⋅     
      ⋅       -1.0 + 0.0im

julia> z_matrix = get_matrix(z)
2×2 Matrix{ComplexF64}:
 1.0+0.0im   0.0+0.0im
 0.0+0.0im  -1.0+0.0im

```
