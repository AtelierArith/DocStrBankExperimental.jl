```
numtype(T)
```

Return the bound type of the interval.

# Examples

```jldoctest
julia> numtype(interval(1, 2))
Float64

julia> numtype(interval(Float32, 1, 2))
Float32
```
