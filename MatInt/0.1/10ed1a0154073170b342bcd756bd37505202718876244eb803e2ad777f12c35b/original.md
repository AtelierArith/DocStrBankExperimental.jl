`baseInt(m::Matrix{<:Integer})`

returns  a matrix in  Hermite normal form  whose rows forms  a basis of the integral  row space of `m`, i.e. of the set of integral linear combinations of the rows of `m`.

```julia-repl
julia> m=[1 2 7;4 5 6;10 11 19]
3×3 Matrix{Int64}:
  1   2   7
  4   5   6
 10  11  19

julia> baseInt(m)
3×3 Matrix{Int64}:
 1  2   7
 0  3   7
 0  0  15
```
