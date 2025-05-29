```
cartesian2morton(c::Vector) -> m::Integer
```

Given a 2-D Cartesian coordinate, return the corresponding Morton number.

# Examples

```jldoctest
julia> cartesian2morton([5,2])
19
```
