```
FacetCache(grid::Grid)
FacetCache(dh::AbstractDofHandler)
```

Create a cache object with pre-allocated memory for the nodes, coordinates, and dofs of a cell suitable for looping over *facets* in a grid. The cache is updated for a new facet by calling `reinit!(cache, fi::FacetIndex)`.

**Methods with `fc::FacetCache`**

  * `reinit!(fc, fi)`: reinitialize the cache for facet `fi::FacetIndex`
  * `cellid(fc)`: get the current cellid
  * `getnodes(fc)`: get the global node ids of the *cell*
  * `getcoordinates(fc)`: get the coordinates of the *cell*
  * `celldofs(fc)`: get the global dof ids of the *cell*
  * `reinit!(fv, fc)`: reinitialize [`FacetValues`](@ref)

See also [`FacetIterator`](@ref).
