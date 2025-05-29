`echelon!(m::AbstractMatrix)`

puts  `m` in echelon  form in-place and  returns: 

(`m`, indices of linearly independent  rows of original `m`)

The  echelon form transforms the  rows of m into  a particular basis of the rowspace. The first non-zero element of each line is 1, and such an element is also the only non-zero in its column. This function works in any field.

```julia-repl
julia> m=[1 1 1 0;0 1 1 0;1 0 0 0;1 1 1 1]//1
4×4 Matrix{Rational{Int64}}:
 1  1  1  0
 0  1  1  0
 1  0  0  0
 1  1  1  1

julia> echelon!(m)
(Rational{Int64}[1 0 0 0; 0 1 1 0; 0 0 0 1; 0 0 0 0], [1, 2, 4])
```
