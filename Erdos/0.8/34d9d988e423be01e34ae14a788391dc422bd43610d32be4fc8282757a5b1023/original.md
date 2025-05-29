```
graph{G<:AGraph}(n, edgelist::Vector{Tuple{Int,Int}},
    G = Graph)
```

Build a graph with `n` vertices, of type `G`, and given `edgelist`.
