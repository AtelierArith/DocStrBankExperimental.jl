```
is_left_to_right(p::PointRecord)
is_left_to_right(points, inds = :)
```

Check whether the scanner mirror was moving left to right relative to the in-track direction (increasing scan angle) when the point was recorded.

See also: [`PointRecord`](@ref), [`scan_angle`](@ref), [`is_right_to_left`](@ref), [`is_edge_of_line`](@ref)
