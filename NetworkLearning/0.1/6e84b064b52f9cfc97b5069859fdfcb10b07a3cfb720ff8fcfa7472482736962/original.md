```
strip_adjacency(a)
```

Function that removes adjancency information (i.e. matrix, graph or other data) from adjacency objects and returns a `PartialAdjacency` that can be used in conjunction with the `adjacency` function to build a new adjacency object.

# Examples

```
julia> using NetworkLearning, LightGraphs

julia> A = [0 1 0; 1 0 0; 0 0 0];

julia> Am = adjacency(A)
Matrix adjacency, 3 obs

julia> Ac = adjacency(x->x,A)
Computable adjacency

julia> Sm = strip_adjacency(Am)
Partial adjacency, not computable

julia> adjacency(Sm, A) # Sm has to be used with a matrix
Matrix adjacency, 3 obs

julia> Sc = strip_adjacency(Ac)
Partial adjacency, not computable

julia> adjacency(Sc, A) # Sc can be use with any data; calls f(A) where f = x->x
Matrix adjacency, 3 obs
```
