```julia
struct RawFacet{T}
```

A complex facet as part to the input to TetGen.

  * `polygonlist::Vector{Vector{Int32}}`: Polygons given as arrays of indices which point into the pointlist array describing the input points.

  * `holelist::Matrix`: Array of points given by their coordinates marking polygons describing holes in the facet.
