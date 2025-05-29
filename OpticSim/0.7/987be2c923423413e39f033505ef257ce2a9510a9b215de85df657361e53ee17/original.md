Datatype representing an ordered series of disjoint intervals on a ray. An arbitrary array of `Interval`s can be input to the constructor and they will automatically be processed into a valid `DisjointUnion` (or a single [`Interval`](@ref) if appropriate).

```julia
DisjointUnion(intervals::AbstractVector{Interval{R}})
```
