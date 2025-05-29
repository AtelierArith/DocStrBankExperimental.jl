```
triangulate([Int32,] [FloatType=Float64,] points; [tol=eps(FloatType),])
```

Computes a triangulation of a set of points using the Delaunator algorithm. This is designed for quick graphics applications and speed rather than exact computational geometry.

## Inputs

  * `points` is any type that has integer indexing and length supported. In addition, `p = points[i]` should    be a type where `p[1]` and `p[2]` are the x, y coordinates of p. Or you need to define the functions    `Delaunator.getX(p), Delaunator.getY(p)` for your own type p. 

    If you wish to use a a matrix to give the point information, [`PointsFromMatrix`](@ref)
  * `tol` is used to determine when points are sufficiently close not to include

## Return value

A triangulation, with methods to explore edges, hull points, dual cells.

See also [`basictriangulation`](@ref)
