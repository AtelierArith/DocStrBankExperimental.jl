```
cartesian3morton(c::AbstractVector) -> m::Integer
```

Given a 3-D Cartesian coordinate, return the corresponding Morton number.

# Examples

```jldoctest
julia> cartesian3morton([5,2,1])
67
```
