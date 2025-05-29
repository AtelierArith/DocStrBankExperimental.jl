```
adjacency([a,data])
```

Constructs an adjacency object. If `a` is a `AbstractMatrix`, `AbstractGraph` or  `Tuple`, it will return usable adjacencies. If `a` is a `Function` or `PartialAdjacency`, `data` has to be present. If both arguments are missing,  the function returns an `EmptyAdjacency`.

# Examples

```
julia> using NetworkLearning, LightGraphs

julia> A = [0 1 0; 1 0 0; 0 0 0];

julia> Am = adjacency(A)
Matrix adjacency, 3 obs

julia> Ag = adjacency(Graph(A))
Graph adjacency, 3 obs

julia> Ac = adjacency(x->x,A)
Computable adjacency
```
