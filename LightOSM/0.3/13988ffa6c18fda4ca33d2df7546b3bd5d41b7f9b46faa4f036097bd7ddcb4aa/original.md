```
weights_from_path(g::OSMGraph{U,T,W}, path::Vector{T}; weights=g.weights)::Vector{W} where {U <: DEFAULT_OSM_INDEX_TYPE,T <: DEFAULT_OSM_ID_TYPE,W <: Real}
```

Extracts edge weights from a path using the weight matrix stored in `g.weights` unless a different matrix is passed to the `weights` kwarg.

# Arguments

  * `g::OSMGraph`: Graph container.
  * `path::Vector{T}`: Array of OpenStreetMap node ids.
  * `weights=g.weights`: the matrix that the edge weights are extracted from. Defaults to `g.weights`.

# Return

  * `Vector{W}`: Array of edge weights, distances are in km, time is in hours.
