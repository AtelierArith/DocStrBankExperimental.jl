```
surfaceintersection(obj::CSGTree{T}, r::AbstractRay{T,N})
```

Calculates the intersection of `r` with CSG object, `obj`.

Returns an [`EmptyInterval`](@ref) if there is no intersection, an [`Interval`](@ref) if there is one or two intersections and a [`DisjointUnion`](@ref) if there are more than two intersections.

The ray is intersected with the [`LeafNode`](@ref)s that make up the CSG object and the resulting `Interval`s and `DisjointUnion`s are composed with the same boolean operations to give a final result. The ray is transformed by the inverse of the transform associated with the leaf node to put it in *object space* for that node before the intersection is carried out, typically this *object space* is centered at the origin, but may differ for each primitive.

Some intersections are culled without actually evaluating them by first checking if the ray intersects the [`BoundingBox`](@ref) of each node in the [`CSGTree`](@ref), this can substantially improve performance in some cases.
