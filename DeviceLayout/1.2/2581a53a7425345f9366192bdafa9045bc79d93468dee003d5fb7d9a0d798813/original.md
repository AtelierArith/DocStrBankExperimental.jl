```
footprint(geo::AbstractGeometry)
footprint(geos)
```

Return the footprint of `geo`.

By default, this falls back to [`bounds(geo)`](@ref), but it may be any single `GeometryEntity` fully containing `geo`.

The footprint of a collection or iterator `geos` is `bounds(geos)`.
