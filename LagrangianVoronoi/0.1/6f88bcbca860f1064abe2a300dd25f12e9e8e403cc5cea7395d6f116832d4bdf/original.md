```
point_value(grid::VoronoiGrid, x::RealVector, fun::Function)
```

Obtain the interpolation of a function `fun` defined on polygons at an arbitrary point `x`. This is a slow code and should never be used in perfomance-critical areas.
