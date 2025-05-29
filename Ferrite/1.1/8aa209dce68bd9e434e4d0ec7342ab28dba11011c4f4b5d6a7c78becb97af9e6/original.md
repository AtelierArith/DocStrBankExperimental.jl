```
CellCache(grid::Grid)
CellCache(dh::AbstractDofHandler)
```

Create a cache object with pre-allocated memory for the nodes, coordinates, and dofs of a cell. The cache is updated for a new cell by calling `reinit!(cache, cellid)` where `cellid::Int` is the cell id.

**Methods with `CellCache`**

  * `reinit!(cc, i)`: reinitialize the cache for cell `i`
  * `cellid(cc)`: get the cell id of the currently cached cell
  * `getnodes(cc)`: get the global node ids of the cell
  * `getcoordinates(cc)`: get the coordinates of the cell
  * `celldofs(cc)`: get the global dof ids of the cell
  * `reinit!(fev, cc)`: reinitialize [`CellValues`](@ref) or [`FacetValues`](@ref)

See also [`CellIterator`](@ref).
