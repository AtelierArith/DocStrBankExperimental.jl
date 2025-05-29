```
bregions!(builder::SimplexGridBuilder,grid,regionlist;facetregions=nothing)
```

Add all boundary facets of `grid` with region numbers in region list  to geometry description. The optional parameter `facetregions` allows to overwrite the numbers in `regionlist`.
