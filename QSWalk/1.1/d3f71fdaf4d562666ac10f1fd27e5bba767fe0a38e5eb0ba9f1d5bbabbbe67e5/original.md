```
ketbra(irow, icol, size)
```

Return matrix acting on `size`-dimensional vector space, `irow`, `icol` = 1, 2, ..., `size`. The matrix consists of single non-zero element equal to one, located at position (`irow`, `icol`).

# Examples

```jldoctest; setup = :(using QSWalk)
julia> ketbra(1, 2, 3)
3×3 SparseArrays.SparseMatrixCSC{Int64,Int64} with 1 stored entry:
  [1, 2]  =  1

```
