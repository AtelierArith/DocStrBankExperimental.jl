```
gridpoints_in_polygon(poly::AbstractArray{<:AbstractPolygon},
    grid_x::AbstractArray, grid_y::AbstractArray)
```

Return a `BitArray` with `true` for points lying in some polygon in `poly`.

The `BitArray` values correspond to points `(x, y)` with `x ∈ grid_x`, `y ∈ grid_y`, starting from the lower left.

All polygons should have the same orientation (clockwise or counterclockwise). A mix (for example to represent "holes") may not give the desired behavior on polygon or hole edges.
