```
collect_periodic_facets(grid::Grid, mset, iset, transform::Union{Function,Nothing}=nothing; tol=1e-12)
```

Match all mirror facets in `mset` with a corresponding image facet in `iset`. Return a dictionary which maps each mirror facet to a image facet. The result can then be passed to [`PeriodicDirichlet`](@ref).

`mset` and `iset` can be given as a `String` (an existing facet set in the grid) or as a `AbstractSet{FacetIndex}` directly.

By default this function looks for a matching facet in the directions of the coordinate system. For other types of periodicities the `transform` function can be used. The `transform` function is applied on the coordinates of the image facet, and is expected to transform the coordinates to the matching locations in the mirror set.

The keyword `tol` specifies the tolerance (i.e. distance and deviation in facet-normals) between a image-facet and mirror-facet, for them to be considered matched.

See also: [`collect_periodic_facets!`](@ref), [`PeriodicDirichlet`](@ref).
