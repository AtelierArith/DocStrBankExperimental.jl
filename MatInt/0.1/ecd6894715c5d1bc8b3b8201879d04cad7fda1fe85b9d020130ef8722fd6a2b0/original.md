`col_hermite_transforms(m::AbstractMatrix{<:Integer})`

The  column Hermite normal form  `H` of the integer  matrix `m` is a column equivalent  lower triangular form. If a *pivot* is the first non-zero entry on  a column of `H` (the quadrant above  right a pivot is zero), pivots are positive  and entries left of a pivot  are nonnegative and smaller than the pivot.  There exists a unique unimodular matrix `c` such that `m*c==H`. The function  `col_hermite_transforms`  returns  a  named tuple with components `.normal=H` and `.coltrans=c`.

```julia-repl
julia> m=[1 15 28;4 5 6;7 8 9]
3×3 Matrix{Int64}:
 1  15  28
 4   5   6
 7   8   9

julia> n=col_hermite_transforms(m)
(normal = [1 0 0; 0 1 0; 0 1 3], coltrans = [-1 13 -50; 2 -27 106; -1 14 -55], rank = 3, signdet = 1)

julia> m*n.coltrans==n.normal
true
```
