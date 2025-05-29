```
function nodes_from_bfs(graph::Graph{T}, source::T;
                        reverse::Bool = false) where T

function nodes_from_bfs(graph::Graph{T}, source::T,
                        destinations::Union{Set{T}, Vector{T}};
                        reverse::Bool = false) where T
```

Returns the `Vector` of nodes in the BFS path from the `source` (optionally, towards the `destinations`). If `reverse=true` returns the reverse order of nodes.
