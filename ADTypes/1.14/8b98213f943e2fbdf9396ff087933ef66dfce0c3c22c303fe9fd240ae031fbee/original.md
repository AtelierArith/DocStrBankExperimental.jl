```
symmetric_coloring(M::AbstractMatrix, ca::ColoringAlgorithm)::AbstractVector{<:Integer}
```

Use algorithm `ca` to construct a symmetrically structurally orthogonal partition of the columns (or rows) of the symmetric matrix `M`.

The result is a coloring vector `c` of length `size(M, 1) == size(M, 2)` such that for every non-zero coefficient `M[i, j]`, at least one of the following conditions holds:

  * column `j` is the only column of its color `c[j]` with a non-zero coefficient in row `i`;
  * column `i` is the only column of its color `c[i]` with a non-zero coefficient in row `j`.
