```
scan_angle(p::PointRecord)
scan_angle(points, inds = :)
```

Obtain the angle (in degrees) of the laser beam that scanned the point. The value is defined as the angle relative to the nadir (i.e. corrected for airplane roll), with 0° pointing straight down, negative values towards the left, and positive values towards the right of the flight path. The values range from −180° to +180° in increments of 0.006° for the PDRFs 6–10, and from −90° to +90° in increments of 1° for the legacy PDRFs 0–5.

See also: [`PointRecord`](@ref), [`is_left_to_right`](@ref), [`is_right_to_left`](@ref), [`is_edge_of_line`](@ref)
