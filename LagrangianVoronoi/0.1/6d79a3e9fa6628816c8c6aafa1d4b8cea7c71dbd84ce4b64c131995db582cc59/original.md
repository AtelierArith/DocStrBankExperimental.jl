```
populate_vogel!(grid::VoronoiGrid{T}; charfun, center, ic!)
```

Populate computational domain with polygons arranged on Vogel spiral. Keyword parameters:

  * `charfun`: the characteristic function; only those areas where `charfun(x) = true` are populated
  * `center`: the center of the spiral
  * `ic!`: the initial condition; `ic!(p)` is called on every polygon *after* the mesh is generated
