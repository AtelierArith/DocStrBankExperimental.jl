```
total_path_weight(g::OSMGraph{U,T,W}, path::Vector{T}; weights=g.weights)::W where {U <: Integer,T <: DEFAULT_OSM_ID_TYPE,W <: Real}
```

Extract total edge weight along a path.

# Arguments

  * `g::OSMGraph`: Graph container.
  * `path::Vector{T}`: Array of OpenStreetMap node ids.
  * `weights=g.weights`: the matrix that the edge weights are extracted from. Defaults to `g.weights`.

# Return

  * `sum::W`: Total path edge weight, distances are in km, time is in hours.
