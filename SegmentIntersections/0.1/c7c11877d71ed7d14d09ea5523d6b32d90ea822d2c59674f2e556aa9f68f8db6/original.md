```
find_intersections(segments::Vector{Segment{T}}; tol=1e-9) where {T<:AbstractFloat}
```

Compute all the intersections between the segments using the Bentley-Ottmann algorithm.

Seting a tolerance value to work for all situations is tricky, so try to play with it if you are finding that not all intersections are found.

# Examples

```jldoctest
julia> segments = [Segment(0,0,5,5), Segment(0,5,5,0)];
julia> intersections = find_intersections(segments)
julia> [Point(2.5, 2.5)]
```
