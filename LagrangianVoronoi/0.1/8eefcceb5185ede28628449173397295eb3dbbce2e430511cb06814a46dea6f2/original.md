```
movingls(::Type{T}, grid::VoronoiGrid, p::VoronoiPolygon, fun; h,  kernel)
```

Finds the Taylor expansion of a given function using moving least squares.  The first argument `T` should be one of following:

  * LinearExpansion
  * QuadraticExpansion
  * CubicExpansion

Polygon `p` is where the Taylor expansion of a function `fun` is computed. A keyword argument `h` is the moving radius. This needs to be sufficiently big, otherwise the Taylor expension may be undefined. Kernel is the weighting function used for defining the (weighted) least squared problem.
