```
ket(index, size)
```

Return `index`-th base (column) vector in the `size`-dimensional vector space. To be consistent with Julia indexing, `index` = 1, 2, ..., `size`.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> ket(1, 2)
2-element SparseArrays.SparseVector{Int64,Int64} with 1 stored entry:
  [1]  =  1
```
