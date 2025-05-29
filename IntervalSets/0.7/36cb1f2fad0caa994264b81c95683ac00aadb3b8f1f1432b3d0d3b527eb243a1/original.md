```
range(i::OpenInterval; length)
range(i::OpenInterval, length::Integer)
```

Constructs a range of a specified length with `step = width(i) / (length + 1)`.

# Examples

```jldoctest
julia> range(iv"(1, 4)", 5)  # Does not contain the endpoints
1.5:0.5:3.5

julia> range(1, 4, 7)
1.0:0.5:4.0
```
