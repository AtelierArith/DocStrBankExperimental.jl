`lnullspaceInt(m::Matrix{<:Integer})

returns a matrix whose rows form a basis of the integral lnullspace of `m`, that  is  of  elements  of  the  left  nullspace  of `m` that have integral entries.

```julia-repl
julia> m=[1 2 7;4 5 6;7 8 9;10 11 19;5 7 12]
5×3 Matrix{Int64}:
  1   2   7
  4   5   6
  7   8   9
 10  11  19
  5   7  12

julia> MatInt.lnullspaceInt(m)
2×5 Matrix{Int64}:
 1  18   -9  2  -6
 0  24  -13  3  -7
```
