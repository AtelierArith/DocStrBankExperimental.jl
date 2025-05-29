`smith(m::AbstractMatrix{<:Integer})`

computes  the Smith normal form  `S` of `m`, the  unique equivalent (in the sense  that  there  exist  unimodular  integer  matrices  `r,  c` such that `r*m*c==S`) diagonal matrix such that `Sᵢ,ᵢ` divides `Sⱼ,ⱼ` for `i≤j`.

```julia-repl
julia> m=[1 15 28 7;4 5 6 7;7 8 9 7]
3×4 Matrix{Int64}:
 1  15  28  7
 4   5   6  7
 7   8   9  7

julia> smith(m)
3×4 Matrix{Int64}:
 1  0  0  0
 0  1  0  0
 0  0  3  0
```
