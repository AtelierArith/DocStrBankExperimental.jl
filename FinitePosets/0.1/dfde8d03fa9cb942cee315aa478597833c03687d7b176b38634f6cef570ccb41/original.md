`CPoset(h::Vector{<:Vector{<:Integer}})`

Creates a poset from a Hasse diagram given as a `Vector` whose `i`-th entry is  the  list  of  indices  which  are immediate successors (covers) of the `i`-th  element, that is `h[i]`  is the list of  `j` such that `i<j` in the poset and such that there is no `k` such that `i<k<j`.

```julia-repl
julia> CPoset([[2,3],[4,5],[4,5],Int[],Int[]])
1<2,3<4,5
```
