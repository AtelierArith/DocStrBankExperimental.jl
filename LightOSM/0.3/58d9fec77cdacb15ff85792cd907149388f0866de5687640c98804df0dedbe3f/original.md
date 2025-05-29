```
nearest_way(g, point, [search_radius])
```

Finds the nearest way from a point using a `SpatialIndexing.jl` R-tree.

The search area is a cube centred on `point` with an edge length of `2 * search_radius`. If  `search_radius` is not specified, it is automatically determined from the distance to the  nearest node. 

A larger `search_radius` will incur a performance penalty as more ways must be checked for  their closest points. Choose this value carefully according to the desired use case.

# Arguments

  * `g::OSMGraph`: Graph container.
  * `point`: Single point as a `GeoLocation` or `[lat, lon, alt]`.
  * `search_radius::AbstractFloat`: Size of cube to search around `point`.

# Return

  * `::Tuple{<:Integer,Float64,EdgePoint}`: If nearest way was found.

      * `::Integer`: Nearest way ID.
      * `::Float64`: Distance to nearest way.
      * `::EdgePoint`: Closest point on the nearest way.
  * `::Tuple{Nothing,Nothing,Nothing}`: If no ways were found within `search_radius`.
