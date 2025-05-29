```
SparseMatrixCOO(m, n, rows, cols, vals)
```

Creates a sparse matrix stored in COO format.

# Examples

```julia-repl
julia> A = SparseMatrixCOO(3, 4, [1, 2, 2, 4], [1, 2, 3, 4], [4.0, 3.0, -2.0, 6.0])
3×4 SparseMatrixCOO{Float64, Int64} with 4 stored entries:
     ┌─────┐
   1 │⠀⠄⠀⠀⠀│ > 0
   3 │⠀⠀⠁⠁⡀│ < 0
     └─────┘
     ⠀1⠀⠀⠀4⠀
     ⠀nz = 4
```
