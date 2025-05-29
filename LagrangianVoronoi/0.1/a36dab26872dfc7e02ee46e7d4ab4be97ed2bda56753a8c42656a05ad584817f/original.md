```
populate_rect!(grid::VoronoiGrid{T}; charfun, ic!)
```

Populate computational domain with Cartesian grid. Keyword parameters:

  * `charfun`: the characteristic function; only those areas where `charfun(x) = true` are populated
  * `ic!`: the initial condition; `ic!(p)` is called on every polygon *after* the mesh is generated
