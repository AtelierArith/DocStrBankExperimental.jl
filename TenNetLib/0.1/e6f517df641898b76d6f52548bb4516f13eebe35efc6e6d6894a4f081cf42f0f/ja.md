```
function nodes_from_bfs(graph::Graph{T}, source::T;
                        reverse::Bool = false) where T

function nodes_from_bfs(graph::Graph{T}, source::T,
                        destinations::Union{Set{T}, Vector{T}};
                        reverse::Bool = false) where T
```

`source`からのBFSパスのノードの`Vector`を返します（オプションで、`destinations`に向かって）。`reverse=true`の場合は、ノードの逆順を返します。
