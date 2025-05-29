```
distance(point_a::AbstractVector, point_b::AbstractVector) -> Float
```

Compute the distance from a point to a line.

This is the distance from the point to its projection on the line.

# Examples

```jldoctest
julia> distance([0, 0], Line([0, 0], [1, 0]))
0.0

julia> round(distance([1, 0], Line([0, 0], [1, 1])), digits=3)
0.707

julia> round(distance([1, 2, 3], Line([-1, 3, 2], [7, 4, 2])), digits=3)
1.978
```
