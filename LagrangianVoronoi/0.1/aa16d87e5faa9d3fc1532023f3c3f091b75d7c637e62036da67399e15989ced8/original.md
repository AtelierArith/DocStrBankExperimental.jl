```
populate_hex!(grid::VoronoiGrid{T}; charfun, ic!)
```

Populate computational domain with polygons arranged in hexagonal grid. Use this initializing method when you are not sure. Keyword parameters:

  * `charfun`: the characteristic function; only those areas where `charfun(x) = true` are populated
  * `ic!`: the initial condition; `ic!(p)` is called on every polygon *after* the mesh is generated
