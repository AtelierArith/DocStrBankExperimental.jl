```
function find_eccentric_central_node(graph::Graph{T}) where T
function find_eccentric_central_node(graph::Graph{T}, nodes::Set{T}) where T
function find_eccentric_central_node(graph::Graph{T}, nodes::Vector{T}) where T
```

Finds the eccentric central node of a `Graph`. Optionally, when `nodes` is specified, finds the central node with respect to the `nodes`.
