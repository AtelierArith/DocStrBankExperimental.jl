```
populate_lloyd!(grid::VoronoiGrid{T}; charfun, niterations, ic!)
```

Populate computational domain with polygons arranged in concentric circles.  Keyword parameters:

  * `charfun`: the characteristic function; only those areas where `charfun(x) = true` are populated
  * `center`: the center of each circle
  * `ic!`: the initial condition; `ic!(p)` is called on every polygon *after* the mesh is generated
