```
sparse_from_lists(nr, nc, tchar, tzero, tone, r, c, v)
```

Create sparse matrix from lists describing the entries.

The vectors `r`, `c`, and `v` have to have the same length and the matrix has entry `v[k]` at `(r[k],c[k])`. Zero entries will be ignored, and multiple entries for the same matrix position raise an error.

The input arguments have the following meaning:

  * `nr::Int`: Number of rows
  * `nc::Int`: Number of columns
  * `tchar`: Field characteristic if `T==Int`
  * `tzero::T`: Number 0 of type `T`
  * `tone::T`:  Number 1 of type `T`
  * `r::Vector{Int}`: Vector of row indices
  * `c::Vector{Int}`: Vector of column indices
  * `v::Vector{T}`: Vector of matrix entries

If `tchar>0`, then the entries in `v` are all replaced by their values mod `tchar`.
