`CPoset(covers::Vector{Tuple{Int,Int}})`

creates a poset representing the transitive closure of the given relations. The  poset is on `1:n` where `n` is the maximum number which appears in the relations.

```julia-repl
julia> CPoset([(6,2),(5,1)])
3,4
5<1
6<2
```
