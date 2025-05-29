```
gps_time(p::PointRecord)
gps_time(points, inds = :)
```

Obtain the GPS time at which a point was recorded for the PDRFs 1 & 3–10, or `missing` if the PDRF does not include a GPS time. Refer to the `has_adjusted_gps_time` field of [`LAS`](@ref) for the interpretation of the time value.

See also: [`PointRecord`](@ref)
