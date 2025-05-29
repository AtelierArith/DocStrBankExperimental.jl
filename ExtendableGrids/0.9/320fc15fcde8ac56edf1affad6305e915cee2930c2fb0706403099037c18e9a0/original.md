function glue(g1,g2;             g1regions=1:num*bfaceregions(g1),             g2regions=1:num*bfaceregions(g2),             interface=0,             tol=1.0e-10)

Merge two grids along their common boundary facets. 

  * g1: First grid to be merged
  * g2: Second grid to be merged
  * g1regions: boundary regions to be used from grid1. Default: all.
  * g2regions: boundary regions to be used from grid2. Default: all.
  * interface: if nonzero, create interface region in new grid, otherwise, ignore
  * tol:  Distance below which two points are seen as identical. Default: 1.0e-10

Deprecated:

  * breg: old notation for interface
