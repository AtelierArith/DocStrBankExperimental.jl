```
surfaceintersection(surf::Surface{T}, r::AbstractRay{T}) where {T}
```

Calculates the intersection of `r` with a surface of any type, `surf`. Note that some surfaces cannot be intersected analytically so must be wrapped in an [`AcceleratedParametricSurface`](@ref) in order to be intersected.

Returns an [`EmptyInterval`](@ref) if there is no [`Intersection`](@ref), an [`Interval`](@ref) if there is one or two intersections and a [`DisjointUnion`](@ref) if there are more than two intersections.
