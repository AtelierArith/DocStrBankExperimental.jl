```
column_coloring(M::AbstractMatrix, ca::ColoringAlgorithm)::AbstractVector{<:Integer}
```

Use algorithm `ca` to construct a structurally orthogonal partition of the columns of `M`.

The result is a coloring vector `c` of length `size(M, 2)` such that for every non-zero coefficient `M[i, j]`, column `j` is the only column of its color `c[j]` with a non-zero coefficient in row `i`.
