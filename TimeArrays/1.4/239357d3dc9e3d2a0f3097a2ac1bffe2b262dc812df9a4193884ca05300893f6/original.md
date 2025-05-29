```
ta_backward_fill([, pattern::Function], t_array::TimeArray) -> TimeArray
```

Return an array where elements that match `pattern` are replaced by nearest previous non-pattern value in `t_array`. By default `pattern` is `isnan` function.

## Examples

```jldoctest
julia> using Dates

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-01-03"), 1.0),
           TimeTick(DateTime("2024-01-07"), NaN),
           TimeTick(DateTime("2024-01-09"), NaN),
           TimeTick(DateTime("2024-01-10"), 5.0),
       ]);

julia> ta_backward_fill(t_array)
4-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-03T00:00:00, 1.0)
 TimeTick(2024-01-07T00:00:00, 1.0)
 TimeTick(2024-01-09T00:00:00, 1.0)
 TimeTick(2024-01-10T00:00:00, 5.0)
```
