```
tree2morton(t::AbstractVector) -> m::Integer
```

Given a quadtree coordinate, return the corresponding Morton number.

# Examples

```jldoctest
julia> tree2morton([2,1,3])
19
```
