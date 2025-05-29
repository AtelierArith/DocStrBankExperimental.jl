```
scan_angle(Integer, p::PointRecord)
scan_angle(Integer, points, inds = :)
```

Obtain the “raw” scan angle of a point record as a signed 8- or 16-bit integer, depending on the PDRF. The values correspond to increments of 0.006° for the PDRFs 6–10, and increments of 1° for the legacy PDRFs 0–5.

See also: [`PointRecord`](@ref), [`is_left_to_right`](@ref), [`is_right_to_left`](@ref), [`is_edge_of_line`](@ref)
