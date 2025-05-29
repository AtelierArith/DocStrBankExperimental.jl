```
leftendpoint(d::AbstractInterval)
```

The left endpoint of the interval.

# Examples

```jldoctest
julia> leftendpoint(iv"[1,2]")
1

julia> leftendpoint(iv"(2,1)")
2
```
