```
TimeTick{T,V}(x::NamedTuple{_,Tuple{TimeLike,Any}})
TimeTick(x::NamedTuple{_,Tuple{TimeLike,Any}})
```

Constructs a [`TimeTick`](@ref) object from named tuple `x` which contains the timestamp and value.

## Examples

```jldoctest
julia> using Dates

julia> TimeTick{Date,Float64}((timestamp = DateTime("2024-01-01T00:00:00"), value = 100))
TimeTick(2024-01-01, 100.0)

julia> TimeTick((timestamp = DateTime("2024-01-01T00:00:00"), value = 100))
TimeTick(2024-01-01T00:00:00, 100)
```
