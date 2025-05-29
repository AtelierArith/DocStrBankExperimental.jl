```
Geodesic(; semimajor_axis, inv_flattening)
```

A geodesic manifold means that the geometry is on a 3-dimensional ellipsoid, parameterized by `semimajor_axis` ($a$ in mathematical parlance) and `inv_flattening` ($1/f$).

Usually, this is only relevant for area and segmentization calculations.  It becomes more relevant as one grows closer to the poles (or equator).
