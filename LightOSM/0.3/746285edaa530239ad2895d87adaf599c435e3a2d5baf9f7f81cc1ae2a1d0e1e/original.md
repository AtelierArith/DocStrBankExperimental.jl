```
nearest_nodes(g::OSMGraph, node_id::DEFAULT_OSM_ID_TYPE, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, node_ids::Vector{<:DEFAULT_OSM_ID_TYPE}, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, node::Node, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, nodes::AbstractVector{<:Node}, n_neighbours::Integer=1)
```

Finds nearest nodes from a point or `Vector` of points using a `NearestNeighbors.jl` KDTree.

# Arguments

  * `g::OSMGraph`: Graph container.
  * `node`/`nodes`/`node_id`/`node_ids`: Single node or `Vector` of nodes specified by `Node` objects or id.
  * `n_neighbours::Integer`: Number of neighbours to query for each point.

# Return

  * Tuple of neighbours and straight line euclidean distances from each point `([[neighbours]...], [[dists]...])`.   Tuple elements are `Vector{Vector}` if a `Vector` of points is inputted, and `Vector` if a single point is inputted.
