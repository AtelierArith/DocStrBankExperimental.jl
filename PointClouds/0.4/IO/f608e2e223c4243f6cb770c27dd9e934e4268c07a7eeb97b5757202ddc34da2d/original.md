```
is_right_to_left(p::PointRecord)
is_right_to_left(points, inds = :)
```

Check whether the scanner mirror was moving right to left relative to the in-track direction (decreasing scan angle) when the point was recorded.

See also: [`PointRecord`](@ref), [`scan_angle`](@ref), [`is_left_to_right`](@ref), [`is_right_to_left`](@ref)
