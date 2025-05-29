`intersect_rowspaceInt(m::Matrix{<:Integer}, n::Matrix{<:Integer})`

returns  a  matrix  whose  rows  forms  a  basis of the intersection of the integral row spaces of `m` and `n`.

```julia-repl
julia> mat=[1 2 7;4 5 6;10 11 19]; nat=[5 7 2;4 2 5;7 1 4]
3×3 Matrix{Int64}:
 5  7  2
 4  2  5
 7  1  4

julia> intersect_rowspaceInt(mat,nat)
3×3 Matrix{Int64}:
 1  5  509
 0  6  869
 0  0  960
```
