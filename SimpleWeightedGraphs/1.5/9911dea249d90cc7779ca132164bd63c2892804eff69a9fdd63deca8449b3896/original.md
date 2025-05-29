```
SimpleWeightedDiGraph{T,U}
```

A type representing a directed weighted graph with vertices of type `T` and edge weights of type `U`.

# Fields

  * `weights::SparseMatrixCSC{U,T}`: weighted adjacency matrix, indexed by `(dst, src)`

!!! tip "Performance"
    Iteratively adding/removing vertices or edges is not very efficient for this type of graph: better construct the graph in one shot if possible.


# Basic constructors

```
SimpleWeightedDiGraph()  # empty
SimpleWeightedDiGraph(n)  # n vertices, no edges
SimpleWeightedDiGraph(graph)  # from graph
SimpleWeightedDiGraph(adjmx; permute)  # from adjacency matrix, possibly transposed
SimpleWeightedDiGraph(sources, destinations, weights)  # from list of edges
```

Use `methods(SimpleWeightedDiGraph)` for the full list of constructors. When building a new graph from a list of edges, be aware that repeating `(src, dst)` pairs may lead to undefined behavior (e.g. due to floating point errors during weight addition).
