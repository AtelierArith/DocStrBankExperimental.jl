```
populate_rand!(grid::VoronoiGrid{T}; charfun, ic!)
```

Populate computational domain with polygons arranged randomly. This initializing method is not recommended because the mesh will have very low quality. Keyword parameters:

  * `charfun`: the characteristic function; only those areas where `charfun(x) = true` are populated
  * `ic!`: the initial condition; `ic!(p)` is called on every polygon *after* the mesh is generated
