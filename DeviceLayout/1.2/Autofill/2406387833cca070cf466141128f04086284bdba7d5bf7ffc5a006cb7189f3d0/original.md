```
autofill!(cs::AbstractCoordinateSystem,
    filler_cs::AbstractCoordinateSystem,
    grid_x::AbstractArray,
    grid_y::AbstractArray,
    exclusion)
```

Add references to `filler_cs` inside `cs` at grid points not in any `exclusion` polygon.

The `exclusion` argument may be

  * a `Coordinate` denoting an offset used to generate the excluded region from shapes in `cs`
  * a `CoordinateSystem` or `Cell` containing the geometry of the excluded region
  * a `Function` creating a `CoordinateSystem` or `Cell` from `cs`
  * an `AbstractArray{<:AbstractPolygon}`

Returns the origins of references.
