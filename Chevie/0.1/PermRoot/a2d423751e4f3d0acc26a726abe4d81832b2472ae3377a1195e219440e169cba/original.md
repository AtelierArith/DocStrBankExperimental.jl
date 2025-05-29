`bipartite_decomposition(W)`

Returns  a bipartite decomposition `[L,R]` of the indices of the generators of  the  reflection  group  `W`,  such  that `reflection_subgroup(W,L)` and `reflection_subgroup(W,R)` are abelian subgroups, and `W=reflection_subgroup(W,   vcat(L,R))`.   Gives   an   error  if  no  such decomposition is possible.

```julia-repl
julia> bipartite_decomposition(coxgroup(:E,8))
([1, 4, 6, 8], [3, 2, 5, 7])

```
