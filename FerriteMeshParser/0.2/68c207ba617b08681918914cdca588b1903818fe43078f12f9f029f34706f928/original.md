```
create_facetset(
    grid::Ferrite.AbstractGrid, 
    nodeset::Set{Int}, 
    cellset::Union{UnitRange{Int},Set{Int}}=1:getncells(grid)
    )
```

Find the facets in the grid for which all nodes are in `nodeset`. Return them as a `Set{FacetIndex}`. A `cellset` can be given to only look only for faces amongst those cells to speed up the computation.  Otherwise the search is over all cells.

This function is normally only required when calling `get_ferrite_grid` with `generate_facetsets=false`.  The created `facetset` can be added to the grid as `addfacetset!(grid, "facetsetkey", facetset)`
