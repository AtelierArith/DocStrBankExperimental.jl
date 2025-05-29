`hermite_transforms(m::AbstractMatrix{<:Integer})`

The row Hermite normal form `H` of `m` is an upper triangular form with the same  integral rowspace. Further, in  this form, if a  *pivot* is the first non-zero  entry on a row  of `H`, the quadrant  below left a pivot is zero, pivots  are positive and entries above  a pivot are nonnegative and smaller than  the pivot. There exists a (unique  if `m` is of full rank) unimodular matrix  `r` such that `r*m==H`. The function `hermite_transforms` returns a named tuple with components `.normal=H` and `.rowtrans=r`.

```julia-repl
julia> m=[1 15 28;4 5 6;7 8 9]
3×3 Matrix{Int64}:
 1  15  28
 4   5   6
 7   8   9

julia> n=hermite_transforms(m)
(normal = [1 0 1; 0 1 1; 0 0 3], rowtrans = [-2 62 -35; 1 -30 17; -3 97 -55], rank = 3, signdet = 1)

julia> n.rowtrans*m==n.normal
true
```
