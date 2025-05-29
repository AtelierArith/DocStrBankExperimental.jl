```
TimeArray(values::Vector{Pair{T,V}})
TimeArray(values::Vector{Tuple{TimeLike,Any}})
TimeArray(values::Vector{NamedTuple{_,Tuple{T,V}}})
```

Creates a `TimeArray{T,V}` object from `values` and sorts them by date in ascending order.

## Examples

```jldoctest
julia> using Dates

julia> TimeArray([
           DateTime("2024-01-02T00:00:00") => 3,
           DateTime("2024-01-03T00:00:00") => 1,
           DateTime("2024-01-01T00:00:00") => 2,
       ])
3-element TimeArray{DateTime, Int64}:
 TimeTick(2024-01-01T00:00:00, 2)
 TimeTick(2024-01-02T00:00:00, 3)
 TimeTick(2024-01-03T00:00:00, 1)

julia> TimeArray([
           (DateTime("2024-01-02T00:00:00"), 3),
           (DateTime("2024-01-03T00:00:00"), 1),
           (DateTime("2024-01-01T00:00:00"), 2),
       ])
3-element TimeArray{DateTime, Int64}:
 TimeTick(2024-01-01T00:00:00, 2)
 TimeTick(2024-01-02T00:00:00, 3)
 TimeTick(2024-01-03T00:00:00, 1)

julia> TimeArray([
           (time = DateTime("2024-01-02T00:00:00"), value = 3),
           (time = DateTime("2024-01-03T00:00:00"), value = 1),
           (time = DateTime("2024-01-01T00:00:00"), value = 2),
       ])
3-element TimeArray{DateTime, Int64}:
 TimeTick(2024-01-01T00:00:00, 2)
 TimeTick(2024-01-02T00:00:00, 3)
 TimeTick(2024-01-03T00:00:00, 1)
```
