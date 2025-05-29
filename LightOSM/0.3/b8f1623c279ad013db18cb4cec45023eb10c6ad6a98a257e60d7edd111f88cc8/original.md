```
nearest_nodes(g::OSMGraph, point::GeoLocation, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, points::AbstractVector{GeoLocation}, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, point::AbstractVector{<:AbstractFloat}, n_neighbours::Integer=1)
nearest_nodes(g::OSMGraph, points::AbstractVector{<:AbstractVector{<:AbstractFloat}}, n_neighbours::Integer=1)
```

Finds nearest nodes from a point or `Vector` of points using a `NearestNeighbors.jl` KDTree.

# Arguments

  * `g::OSMGraph`: Graph container.
  * `point`/`points`: Single point as a `GeoLocation` or `[lat, lon, alt]`, or a `Vector` of such points
  * `n_neighbours::Integer`: Number of neighbours to query for each point.

# Return

  * Tuple of neighbours and straight line euclidean distances from each point `([[neighbours]...], [[dists]...])`.   Tuple elements are `Vector{Vector}` if a `Vector` of points is inputted, and `Vector` if a single point is inputted.
