```
ph_reduce!(matrix::SparseMatrix; [returnbasis=true])
```

Apply the persistence reduction algorithm to the matrix.

The function returns the values

  * `phsingles::Vector{Vector{Int}}`
  * `phpairs::Vector{Vector{Tuple{Int,Int}}}`
  * `basis::SparseMatrix` (if `returnbasis=true`)

It assumes that `matrix` is strictly upper triangular. The function returns the starting columns for infinite length persistence intervals in `phsingles`, and the birth- and death-columns for finite length persistence intervals in `phpairs`. If the optional argument `returnbasis=true` is given, then the function also returns the computed basis matrix B with `reduced = matrix * B`.
