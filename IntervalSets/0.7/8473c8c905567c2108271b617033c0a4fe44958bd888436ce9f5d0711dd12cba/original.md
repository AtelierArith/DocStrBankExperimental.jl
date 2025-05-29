```
rightendpoint(d::AbstractInterval)
```

The right endpoint of the interval.

# Examples

```jldoctest
julia> rightendpoint(iv"[1,2]")
2

julia> rightendpoint(iv"(2,1)")
1
```
