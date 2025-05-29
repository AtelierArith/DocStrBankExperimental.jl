```
ta_lead(t_array::TimeArray{T,V}, n::Integer) -> TimeArray
```

Shifts the values of `t_array` elements by `n` positions backward. Displaced elements that remain without a value are set to `NaN`.

## Examples

```jldoctest
julia> using Dates

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-03-01"), 1.0),
           TimeTick(DateTime("2024-03-02"), 2.0),
           TimeTick(DateTime("2024-03-03"), 3.0),
           TimeTick(DateTime("2024-03-04"), 4.0),
       ]);

julia> ta_lead(t_array, 2)
4-element TimeArray{DateTime, Float64}:
 TimeTick(2024-03-01T00:00:00, 3.0)
 TimeTick(2024-03-02T00:00:00, 4.0)
 TimeTick(2024-03-03T00:00:00, NaN)
 TimeTick(2024-03-04T00:00:00, NaN)
```
