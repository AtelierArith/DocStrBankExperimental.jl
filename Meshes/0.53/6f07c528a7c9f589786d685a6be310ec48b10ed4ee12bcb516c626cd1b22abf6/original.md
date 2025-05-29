```
Morphological(fun)
```

Morphological transform given by a function `fun` that maps the coordinates of a geometry or a domain to new coordinates (`coords -> newcoords`).

## Examples

```julia
ball = Ball((0, 0), 1)
ball |> Morphological(c -> Cartesian(c.x + c.y, c.y, c.x - c.y))

triangle = Triangle(Point(LatLon(0, 0)), Point(LatLon(0, 45)), Point(LatLon(45, 0)))
triangle |> Morphological(c -> LatLonAlt(c.lat, c.lon, 0.0m))
```

### Notes

By default, only the vertices of the polytopes are transformed, disregarding distortions that occur in manifold conversions. To handle this case, use [`TransformedGeometry`](@ref).
