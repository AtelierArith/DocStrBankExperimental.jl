```
sparse_matrix(::AbstractGate)
```

returns sparse matrix representation of [`AbstractGate`](@ref) objects

# Examples

```jldoctest
julia> sparse_matrix(X)
2×2 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 2 stored entries:
  [2, 1]  =  1.0+0.0im
  [1, 2]  =  1.0+0.0im
```
