```
isrightclosed(d::AbstractInterval)
```

Is the interval closed at the right endpoint?

# Examples

```jldoctest
julia> isrightclosed(iv"[1,2]")
true

julia> isrightclosed(iv"(2,1)")
false
```
