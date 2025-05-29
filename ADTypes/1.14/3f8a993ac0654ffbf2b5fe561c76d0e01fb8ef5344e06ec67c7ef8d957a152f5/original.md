```
row_coloring(M::AbstractMatrix, ca::ColoringAlgorithm)::AbstractVector{<:Integer}
```

Use algorithm `ca` to construct a structurally orthogonal partition of the rows of `M`.

The result is a coloring vector `c` of length `size(M, 1)` such that for every non-zero coefficient `M[i, j]`, row `i` is the only row of its color `c[i]` with a non-zero coefficient in column `j`.
