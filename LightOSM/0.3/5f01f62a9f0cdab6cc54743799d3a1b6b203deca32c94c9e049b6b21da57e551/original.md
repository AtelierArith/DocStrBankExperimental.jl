```
nearest_ways(g, point, [search_radius])
```

Finds nearby ways from a point using a `SpatialIndexing.jl` R-tree.

The search area is a cube centred on `point` with an edge length of `2 * search_radius`. 

A larger `search_radius` will incur a performance penalty as more ways must be checked for  their closest points. Choose this value carefully according to the desired use case.

# Arguments

  * `g::OSMGraph`: Graph container.
  * `point`/`points`: Single point as a `GeoLocation` or `[lat, lon, alt]`.
  * `search_radius::AbstractFloat=0.1`: Size of cube to search around `point`.

# Return

  * `::Tuple{Vector{<:Integer},Vector{Float64},Vector{EdgePoint}}`:

      * `::Vector{<:Integer}`: Nearest way IDs.
      * `::Vector{Float64}`: Distance to each corresponding nearby way.
      * `::Vector{EdgePoint}`: Closest point on each corresponding nearby way.
