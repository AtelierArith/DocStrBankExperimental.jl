```
collect_periodic_facets(grid::Grid, all_facets::Union{AbstractSet{FacetIndex},String,Nothing}=nothing; tol=1e-12)
```

Split all facets in `all_facets` into image and mirror sets. For each matching pair, the facet located further along the vector `(1, 1, 1)` becomes the image facet.

If no set is given, all facets on the outer boundary of the grid (i.e. all facets that do not have a neighbor) is used.

See also: [`collect_periodic_facets!`](@ref), [`PeriodicDirichlet`](@ref).
