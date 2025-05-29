```
gridpoints_in_polygon(poly::AbstractArray{<:AbstractPolygon},
    dx::Coordinate, dy::Coordinate; b=nothing)
```

Return a `BitArray` for the gridpoints in `b` with `true` for gridpoints in `poly`.

Only grid points in the bounding box `b` will be considered; if `b` is `nothing`, then bounds(poly) is used. `dx` and `dy` are the distances between adjacent points on the rectangular grid. The grid points represented by the `BitArray` start from the lower left point `p0 = (m*dx, n*dy)` with `m` and `n` integers and `p0` lying in `b`.

All polygons should have the same orientation (clockwise or counterclockwise). A mix (for example to represent "holes") may not give the desired behavior on polygon or hole edges.
