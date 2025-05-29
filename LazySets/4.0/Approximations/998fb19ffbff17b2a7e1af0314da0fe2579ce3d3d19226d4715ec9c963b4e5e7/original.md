```
overapproximate(P::VPolygon, ::Type{<:LinearMap{N,<:Hyperrectangle}}) where {N}
```

Overapproximate a convex polygon with a minimal-area rotated rectangle.

### Input

  * `P` – convex polygon
  * `LinearMap{N,<:Hyperrectangle}` – target type

### Output

A `LinearMap` of a `Hyperrectangle`.

### Algorithm

This method follows an approach described in [this post](https://gis.stackexchange.com/a/22934), which itself is based on [this post](https://gis.stackexchange.com/a/22904).

Generally, the idea is that the rotated rectangle must share at least one edge with the polygon. Thus, it suffices to try out finitely many rectangles. Some tricks from linear algebra allow to construct the corresponding rotations and rectangles elegantly.
