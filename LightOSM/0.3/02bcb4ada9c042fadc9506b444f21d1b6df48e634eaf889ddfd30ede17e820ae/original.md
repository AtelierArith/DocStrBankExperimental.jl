```
nearest_node(g::OSMGraph, node::Node)
nearest_node(g::OSMGraph, nodes::Vector{<:Node})
nearest_node(g::OSMGraph, node_ids::AbstractVector{<:Integer})
nearest_node(g::OSMGraph, node_id::Integer)
```

Finds the nearest node from a node (specified by the `Node` object or node id) or `Vector` of nodes using a `NearestNeighbors.jl` KDTree. The origin node itself is not included in the results.

# Arguments

  * `g::OSMGraph`: Graph container.
  * `node`/`nodes`/`node_id`/`node_ids`: Single node or `Vector` of nodes specified by `Node` objects or id.

# Return

  * Tuple of neighbours and straight line euclidean distances from each node `([neighbours...], [dists...])`.   Tuple elements are `Vector`sif a `Vector` of nodes is inputted, and numbers if a single point is inputted.
