```
Simplex{D, T<:Real, N}(points::NTuple{N, Point{D, T}})
```

A `Simplex` is a generalization of an N-dimensional tetrahedra and can be thought of as a minimal convex set containing the specified points.

  * A 0-simplex is a point.
  * A 1-simplex is a line segment.
  * A 2-simplex is a triangle.
  * A 3-simplex is a tetrahedron.

Note that this datatype is offset by one compared to the traditional mathematical terminology. So a one-simplex is represented as `Simplex{2,T}`. This is for a simpler implementation.

It applies to infinite dimensions. The structure of this type is designed to allow embedding in higher-order spaces by parameterizing on `T`.
