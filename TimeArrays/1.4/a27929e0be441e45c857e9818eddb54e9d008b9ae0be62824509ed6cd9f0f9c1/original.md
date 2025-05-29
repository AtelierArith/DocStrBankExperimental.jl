```
TimeArray{T,V}(values::AbstractVector)
```

Creates a `TimeArrays{T,V}` from a `values` that contains any elements that can be passed to [`TimeTick{T,V}`](@ref TimeTick) constructors.

!!! warning
    This approach greatly reduces performance. Use at your own discretion.


## Examples

```jldoctest
julia> using Dates

julia> values = [
           TimeTick(Date("2024-01-02"), 3.0),
           (DateTime("2024-01-03"), 1.0),
           Date("2024-01-01") => 2,
       ];

julia> TimeArray{Date,Int64}(values)
3-element TimeArray{Date, Int64}:
 TimeTick(2024-01-01, 2)
 TimeTick(2024-01-02, 3)
 TimeTick(2024-01-03, 1)
```
