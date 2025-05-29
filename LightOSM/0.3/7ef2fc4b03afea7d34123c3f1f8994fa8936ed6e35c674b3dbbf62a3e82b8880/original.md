```
nearest_node(g::OSMGraph, point::GeoLocation)
nearest_node(g::OSMGraph, points::Vector{GeoLocation})
nearest_node(g::OSMGraph, point::AbstractVector{<:AbstractFloat})
nearest_node(g::OSMGraph, points::AbstractVector{<:AbstractVector{<:AbstractFloat}})
```

Finds the nearest node from a point (specified by a `GeoLocation` or set of Latitude Longitude coordinates) or `Vector` of points using a `NearestNeighbors.jl` KDTree.

# Arguments

  * `g::OSMGraph`: Graph container.
  * `point`/`points`: Single point as a `GeoLocation` or `[lat, lon, alt]`, or a `Vector` of such points

# Return

  * Tuple of neighbours and straight line euclidean distances from each point `([neighbours...], [dists...])`.   Tuple elements are `Vector`s if a `Vector` of points is inputted, and numbers if a single point is inputted.
