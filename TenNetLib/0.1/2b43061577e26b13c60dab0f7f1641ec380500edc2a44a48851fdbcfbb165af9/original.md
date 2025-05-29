```
function bfs(graph::Graph{T},
             source::T,
             destination::Union{Nothing, T} = nothing) where T
```

Performs a full BFS starting from the node `source` (and optionally, to the `destination`).

#### Return values

  * `::Dict{T, Int}`: Distances of nodes (key) in the BFS path.
  * `::Dict{T, T}`: Parents of nodes (key) in the BFS path.
