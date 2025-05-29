```
morton2cartesian(m::Integer) -> [x,y]
```

Given a Morton number, return the corresponding 2-D Cartesian coordinates.

# Examples

```jldoctest
julia> morton2cartesian(19)
2-element Array{Int64,1}:
 5
 2
```
