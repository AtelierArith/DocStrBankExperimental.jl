```
mutable struct Graph{T}
    nodes::Set{T}
    edges::Dict{T, Set{T}}
end
```

Undirected graph where nodes are of type `T`.

  * `nodes::Set{T}`: Holds the nodes of the graph.
  * `edges::Dict{T, Set{T}}`: Holds the edges of the graph. For a given node as `key`,  holds all the connected nodes as `value` of the `Dict`.
