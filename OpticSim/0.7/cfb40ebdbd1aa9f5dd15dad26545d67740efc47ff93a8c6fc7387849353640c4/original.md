```
surfaceintersection(bbox::BoundingBox{T}, r::AbstractRay{T,3}) -> Union{EmptyInterval{T},Interval{T}}
```

Calculates the intersection of `r` with an axis-aligned [`BoundingBox`](@ref), `bbox`.

Returns an [`EmptyInterval`](@ref) if there is no intersection or an [`Interval`](@ref) if there is one or two intersections. Note that the uv of the returned intersection is always **0**.
