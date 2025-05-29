```
isrightopen(d::AbstractInterval)
```

Is the interval open at the right endpoint?

# Examples

```jldoctest
julia> isrightopen(iv"[1,2]")
false

julia> isrightopen(iv"(2,1)")
true
```
