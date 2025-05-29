```
TimeArray{T,V}(values::Vector{TimeTick})
TimeArray(values::Vector{TimeTick{T,V}})
```

Creates a `TimeArray{T,V}` object from `values` and sorts them by date in ascending order.

## Examples

```jldoctest
julia> using Dates

julia> values = [
           TimeTick(DateTime("2022-1-1T00:00:00"), 3),
           TimeTick(DateTime("2023-1-1T00:00:00"), 1),
           TimeTick(DateTime("2021-1-1T00:00:00"), 2),
       ];

julia> TimeArray{Date,Float64}(values)
3-element TimeArray{Date, Float64}:
 TimeTick(2021-01-01, 2.0)
 TimeTick(2022-01-01, 3.0)
 TimeTick(2023-01-01, 1.0)

julia> TimeArray(values)
3-element TimeArray{DateTime, Int64}:
 TimeTick(2021-01-01T00:00:00, 2)
 TimeTick(2022-01-01T00:00:00, 3)
 TimeTick(2023-01-01T00:00:00, 1)
```
