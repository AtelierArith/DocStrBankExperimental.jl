```
is_synthetic(p::PointRecord)
is_synthetic(points, inds = :)
```

Check whether the point is marked as obtained through “synthetic” means (e.g. photogrammetry) rather than direct measurement with a laser pulse.

See also: [`PointRecord`](@ref), [`classification`](@ref), [`is_key_point`](@ref), [`is_overlap`](@ref), [`is_withheld`](@ref)
