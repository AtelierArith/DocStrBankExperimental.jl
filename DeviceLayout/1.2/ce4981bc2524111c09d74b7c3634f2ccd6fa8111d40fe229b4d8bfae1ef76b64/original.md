```
center(geo::AbstractGeometry)
center(geos)
```

Return the center of the bounding rectangle [`bounds(geo)`](@ref) or `bounds(geos)`.

Will not throw an `InexactError` even if `geo` has integer coordinates, but instead return floating point coordinates.

See also: [`lowerleft`](@ref), [`upperright`](@ref).
