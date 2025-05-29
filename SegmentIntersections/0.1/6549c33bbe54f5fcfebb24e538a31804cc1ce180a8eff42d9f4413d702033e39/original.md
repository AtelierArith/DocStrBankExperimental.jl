```
find_intersections_brute(segments::Vector{Segment{T}}) where {T<:AbstractFloat}
```

Compute all the intersections between the segments performing a brute force algorithm O(n^2). This is the O(N^2) brute force version in which we test all segments against all segments for intersections. This method is faster than the BentleyOttman one when there are few points and lots of intersections.

# Examples

```jldoctest
julia> segments = [Segment(0,0,5,5), Segment(0,5,5,0)];
julia> intersections = find_intersections_brute(segments)
julia> [Point(2.5, 2.5)]
```
