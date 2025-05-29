```
closestintersection(a::Union{EmptyInterval{T},Interval{T},DisjointUnion{T}}, ignorenull::Bool = true) -> Union{Nothing,Intersection{T,3}}
```

Returns the closest [`Intersection`](@ref) from an [`Interval`](@ref) or [`DisjointUnion`](@ref). Ignores intersection with null interfaces if `ignorenull` is true. Will return `nothing` if there is no valid intersection.
