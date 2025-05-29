```
angular_distance(point₃::Point, points::Vector{Points{T}}) where T<:Float64
```

Return the `angular_distance` [deg] from point₃ [deg] to the closest point on a an set of points representing an set of arcs.

The `angular_distance` does not change sign when being left or right of the arc.
