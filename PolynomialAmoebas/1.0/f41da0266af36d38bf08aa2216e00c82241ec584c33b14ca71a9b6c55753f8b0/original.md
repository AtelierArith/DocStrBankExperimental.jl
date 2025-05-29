```
TropicalCurve(tropicalpoly)
TropicalCurve(tropicalpoly, newton_polygon::NewtonPolygon)
```

Computes a Tropical planar curve. A curce is represented as a vector of `vertices`, a vector of `segments` between vertices and `halfrays` starting from a node in a specify direction.

You can visualize a `TropicalCurve` `curve` by using `Plots.jl` via `plot(curve)`.

```
TropicalCurve(realpoly)
```

The polynomial will first be converted to a tropical one via [tropicalpolynomial](@ref) and then the curve will be computed as usual.
