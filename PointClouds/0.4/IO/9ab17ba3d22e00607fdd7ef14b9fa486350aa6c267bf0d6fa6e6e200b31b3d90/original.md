```
is_key_point(p::PointRecord)
is_key_point(points, inds = :)
```

Check whether the point is marked as a *key point* that should not be removed when reducing the point density.

See also: [`PointRecord`](@ref), [`classification`](@ref), [`is_overlap`](@ref), [`is_synthetic`](@ref), [`is_withheld`](@ref)
