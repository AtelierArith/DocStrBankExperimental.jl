`independent_rows(m::AbstractMatrix)`

returns  a vector of the  indices of a set  of independent rows of `m` (the lexicographically first such set).

```julia-repl
julia> m=[1 2;2 4;5 6]
3×2 Matrix{Int64}:
 1  2
 2  4
 5  6

julia> independent_rows(m)
2-element view(::Vector{Int64}, 1:2) with eltype Int64:
 1
 3
```
