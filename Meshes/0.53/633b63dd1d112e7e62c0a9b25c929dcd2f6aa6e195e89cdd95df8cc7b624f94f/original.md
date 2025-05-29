```
Box(min, max)
```

A (geodesic) box with `min` and `max` points on a given manifold.

## Examples

Construct a 3D box using points with Cartesian coordinates:

```julia
Box((0, 0, 0), (1, 1, 1))
```

Likewise, construct a 2D box on the plane:

```julia
Box((0, 0), (1, 1))
```

Construct a geodesic box on the ellipsoid:

```julia
Box(Point(LatLon(0, 0)), Point(LatLon(1, 1)))
```
