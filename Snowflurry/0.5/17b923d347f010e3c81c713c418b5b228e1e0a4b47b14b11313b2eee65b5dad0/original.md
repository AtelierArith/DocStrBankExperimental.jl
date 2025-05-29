```
sparse(x::AbstractOperator)
```

Returns a SparseOperator representation of x.

# Examples

```jldoctest
julia> z = sparse(sigma_z())
(2, 2)-element Snowflurry.SparseOperator:
Underlying data ComplexF64:
 1.0 + 0.0im        ⋅     
      ⋅       -1.0 + 0.0im
```
