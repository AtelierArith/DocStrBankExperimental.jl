```
proj(index, size)
```

Return projector onto `index`-th base vector in `size`-dimensional vector space, with `index` = 1, 2, ..., `size`. This is equivalent to `ketbra(index, index, size)`.

```jldoctest; setup = :(using QSWalk)
julia> proj(1, 2)
2×2 SparseArrays.SparseMatrixCSC{Int64,Int64} with 1 stored entry:
  [1, 1]  =  1
```
