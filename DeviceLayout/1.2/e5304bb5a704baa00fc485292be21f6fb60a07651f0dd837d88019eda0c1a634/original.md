```
bounds(geo::AbstractGeometry)
bounds(geo0::AbstractGeometry, geo1::AbstractGeometry, geo::AbstractGeometry...)
bounds(geos)
```

Return the minimum bounding `Rectangle` for `geo` or a collection/iterator `geos`.

If `geo` is empty or has no extent, a rectangle with zero width and height is returned.

For a collection or a structure that may contain multiple entities and references to other structures, geometries with bounds having zero width and height are excluded from the calculation.
