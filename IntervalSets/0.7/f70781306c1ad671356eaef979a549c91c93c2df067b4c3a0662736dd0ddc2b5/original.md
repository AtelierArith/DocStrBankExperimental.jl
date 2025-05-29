```
endpoints(d::AI) where AI<:AbstractInterval
```

A tuple containing the left and right endpoints of the interval.

# Examples

```jldoctest
julia> endpoints(iv"[1,2]")
(1, 2)

julia> endpoints(iv"(2,1)")
(2, 1)
```
