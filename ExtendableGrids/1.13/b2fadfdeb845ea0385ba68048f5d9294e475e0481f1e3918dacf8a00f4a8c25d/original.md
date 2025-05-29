```
glue(g1,g2;
     g1regions=1:num_bfaceregions(g1),
     g2regions=1:num_bfaceregions(g2),
     interface=0,
     warnonly = false,
     tol=1.0e-10,
     naive=false)
```

Merge two grids along their common boundary facets. 

  * g1: First grid to be merged
  * g2: Second grid to be merged
  * g1regions: boundary regions to be used from grid1. Default: all.
  * g2regions: boundary regions to be used from grid2. Default: all.
  * interface: if nonzero, create interface region in new grid, otherwise, ignore
  * strict: Assume all bfaces form specified regions shall be matched, throw error on failure
  * tol:  Distance below which two points are seen as identical. Default: 1.0e-10
  * naive: use naive quadratic complexity matching (for checking backward compatibility). Default: false

Deprecated:

  * breg: old notation for interface
