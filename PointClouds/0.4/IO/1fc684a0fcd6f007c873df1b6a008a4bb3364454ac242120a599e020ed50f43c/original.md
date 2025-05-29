```
is_overlap(p::PointRecord)
is_overlap(points, inds = :)
```

Check whether the point is marked as *overlap*, e.g. of two flight paths. This is recorded as a classification (class 12) or as a separate flag (PDRFs 6–10 only) to allow for further classification of overlap points.

See also: [`PointRecord`](@ref), [`classification`](@ref), [`is_key_point`](@ref), [`is_synthetic`](@ref), [`is_withheld`](@ref)
