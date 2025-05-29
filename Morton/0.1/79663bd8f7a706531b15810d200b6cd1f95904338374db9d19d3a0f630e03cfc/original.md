```
morton3cartesian(m::Integer) -> [x,y,z]
```

Given a Morton number, return the corresponding 3-D Cartesian coordinates.

# Examples

```jldoctest
julia> morton3cartesian(67)
3-element Array{Int64,1}:
 5
 2
 1
```
