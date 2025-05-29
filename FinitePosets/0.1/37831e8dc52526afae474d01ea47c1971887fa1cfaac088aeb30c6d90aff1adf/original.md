`Poset(covers::Vector{Tuple{T,T}}) where T`

creates a poset representing the transitive closure of the given relations. The  poset is on the elements which appear in the relations.

```julia-repl
julia> Poset([(:a,:b),(:d,:c)])
a<b
d<c
```
