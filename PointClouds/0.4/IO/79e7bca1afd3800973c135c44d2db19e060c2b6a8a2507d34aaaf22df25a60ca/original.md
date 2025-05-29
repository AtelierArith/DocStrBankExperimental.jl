```
is_withheld(p::PointRecord)
is_withheld(points, inds = :)
```

Check whether the point is marked as *withheld*/deleted and should be skipped in further processing.

See also: [`PointRecord`](@ref), [`classification`](@ref), [`is_key_point`](@ref), [`is_overlap`](@ref), [`is_synthetic`](@ref)
