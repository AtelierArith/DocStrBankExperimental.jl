```
doesintersect(bbox::BoundingBox{T}, r::AbstractRay{T,3}) -> Bool
```

Tests whether `r` intersects an axis-aligned [`BoundingBox`](@ref), `bbox`.
