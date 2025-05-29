```
tree3morton(t::AbstractVector) -> m::Integer
```

Given a octree coordinate, return the corresponding Morton number.

# Examples

```jldoctest
julia> tree3morton([2,1,3])
67
```
