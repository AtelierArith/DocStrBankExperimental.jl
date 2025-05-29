`col_hermite(m::AbstractMatrix{<:Integer})`

returns  the column Hermite  normal form `H`  of the integer  matrix `m`, a column equivalent lower triangular form. If a *pivot* is the first non-zero entry on a column of `H` (the quadrant above right a pivot is zero), pivots are  positive and entries left of a  pivot are nonnegative and smaller than the pivot. There exists a unique unimodular matrix `c` such that `m*c==H`.

```julia-repl
julia> m=[1 15 28;4 5 6;7 8 9]
3×3 Matrix{Int64}:
 1  15  28
 4   5   6
 7   8   9

julia> col_hermite(m)
3×3 Matrix{Int64}:
 1  0  0
 0  1  0
 0  1  3
```
