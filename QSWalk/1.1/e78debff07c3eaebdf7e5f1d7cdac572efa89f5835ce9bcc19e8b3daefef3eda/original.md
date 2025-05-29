```
bra(index, size)
```

Return `index`-th base row vector in the `size`-dimensional vector space, with `index` = 1, 2, ..., `size`.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> bra(1, 2)
1×2 LinearAlgebra.Adjoint{Int64,SparseArrays.SparseVector{Int64,Int64}}:
 1  0
```
