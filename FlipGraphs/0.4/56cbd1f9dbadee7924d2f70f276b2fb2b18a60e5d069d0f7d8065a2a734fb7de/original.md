```
distances(adjacency_matrix :: Matrix{T}) :: Matrix{T} where T<:Integer
```

Compute the shortest distance from any vertex to any other vertex in the graph for the given `adjacency_matrix`.

Return a `Matrix` whose entry at `(i,j)` is the length of a shortest path from `i` to `j`.

The Graph has to be connected. This method uses *Seidels APSP-Algorithm*.
