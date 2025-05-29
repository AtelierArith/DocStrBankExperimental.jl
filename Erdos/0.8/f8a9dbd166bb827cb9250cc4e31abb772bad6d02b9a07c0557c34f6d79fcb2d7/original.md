```
minimum_spanning_tree{T<:Real}(
    g, distmx::AbstractMatrix{T} = weights(g)
)
```

Performs [Kruskal's algorithm](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm) on a connected, undirected graph `g`, having adjacency matrix `distmx`, and computes minimum spanning tree. Returns a `Vector{KruskalHeapEntry}`, that contains the containing edges and its weights.
