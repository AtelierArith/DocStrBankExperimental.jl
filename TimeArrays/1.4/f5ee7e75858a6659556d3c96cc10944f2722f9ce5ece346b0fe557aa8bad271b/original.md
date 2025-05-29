```
ta_ema(t_array::TimeArray, window::Integer) -> TimeArray
```

Applies [Exponential Moving Average](https://en.wikipedia.org/wiki/Exponential_smoothing) algorithm with window size `n` to the elements of `t_array`.

## Examples

```jldoctest
julia> using Dates

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-01-02"), 1.0),
           TimeTick(DateTime("2024-01-03"), 2.0),
           TimeTick(DateTime("2024-01-05"), 3.0),
           TimeTick(DateTime("2024-01-06"), 4.0),
           TimeTick(DateTime("2024-01-09"), 5.0),
       ]);

julia> ta_ema(t_array, 3)
5-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-02T00:00:00, 1.0)
 TimeTick(2024-01-03T00:00:00, 1.5)
 TimeTick(2024-01-05T00:00:00, 2.25)
 TimeTick(2024-01-06T00:00:00, 3.125)
 TimeTick(2024-01-09T00:00:00, 4.0625)
```
