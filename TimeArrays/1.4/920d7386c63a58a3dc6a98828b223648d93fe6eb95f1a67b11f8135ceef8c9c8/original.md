```
TimeTick{T,V}(x::Tuple{TimeLike,Any})
TimeTick(x::Tuple{T,V})
```

Constructs a [`TimeTick`](@ref) object from tuple `x` which contains the timestamp and value.

## Examples

```jldoctest
julia> using Dates

julia> TimeTick{Date,Float64}((DateTime("2024-01-01T00:00:00"), 100))
TimeTick(2024-01-01, 100.0)

julia> TimeTick((DateTime("2024-01-01T00:00:00"), 100))
TimeTick(2024-01-01T00:00:00, 100)
```
