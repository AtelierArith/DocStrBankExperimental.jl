```
angle_between(u::AbstractVector, v::AbstractVector) -> Float
```

Compute the angle between two vectors. The angle is returned in radians.

# Examples

```jldoctest
julia> angle_between([1, 0], [1, 0])
0.0

julia> round(angle_between([1,1], [1,0]), digits=3)
0.785

julia> round(angle_between([1, 0], [0, 1]), digits=3)
1.571

julia> round(angle_between([-1, 0], [1, 0]), digits=3)
3.142

julia> round(angle_between([1,0,0], [1,1,1]), digits=3)
0.955
```
