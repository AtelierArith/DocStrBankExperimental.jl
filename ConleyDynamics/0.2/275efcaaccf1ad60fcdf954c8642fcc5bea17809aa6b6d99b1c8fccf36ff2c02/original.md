```
SparseMatrix{T}
```

Composite data type for a sparse matrix with entries of type `T`.

The struct has the following fields:

  * `const nrow::Int`: Number of rows
  * `const ncol::Int`: Number of columns
  * `const char::Int`: Characteristic of type `T`
  * `const zero::T`: Number 0 of type `T`
  * `const one::T`:  Number 1 of type `T`
  * `entries::Vector{Vector{T}}`: Matrix entries corresponding to `columns`
  * `columns::Vector{Vector{Int}}`: `column[k]` points to nonzero entries in column k
  * `rows::Vector{Vector{Int}}`: `rows[k]` points to nonzero entries in the k-th row
