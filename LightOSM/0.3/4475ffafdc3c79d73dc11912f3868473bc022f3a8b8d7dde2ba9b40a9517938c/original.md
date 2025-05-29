```
set_dijkstra_state!(g::OSMGraph, src::Union{Integer,Vecotr{<:Integer}, weights::AbstractMatrix; cost_adjustment::Function=(u, v, parents) -> 0.0)
```

Compute and set the dijkstra parent states for one or multiple src vertices. Threads are used for multiple srcs. Note, computing dijkstra states for all vertices is a O(V² + ElogV) operation, use on large graphs with caution.
