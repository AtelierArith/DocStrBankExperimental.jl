```
updatenormal!(
    self::SurfaceNormal,
    XYZ::AbstractVecOrMat{<:Real},
    tangents::AbstractMatrix{<:Real},
    feid::IT,
    qpid::IT,
) where {IT}
```

Update the surface normal vector.

Returns the normal vector (stored in the cache).
