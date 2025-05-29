```
ta_rolling(f::Function, t_array::TimeArray, n::Int; kw...) -> TimeArray
```

Applies function `f` in a sliding window with window size `n` to the elements of `t_array`. Function `f` must accept a vector with elements of type `V` as input and return a new value, which will be assigned to the corresponding timestamp of each window.

## Keyword arguments

  * `observations::Integer = n`: Number of observations in the rolling window to calculate the value (otherwise `NaN`).

Function signature:

```julia
f(x::AbstractVector{V})::Any = ...
```

## Examples

```jldoctest
julia> using Dates

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-01-01"), 1.0),
           TimeTick(DateTime("2024-01-03"), 2.0),
           TimeTick(DateTime("2024-01-04"), 3.0),
           TimeTick(DateTime("2024-01-07"), 4.0),
           TimeTick(DateTime("2024-01-09"), 5.0),
       ]);

julia> ta_rolling(sum, t_array, 3)
5-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, NaN)
 TimeTick(2024-01-03T00:00:00, NaN)
 TimeTick(2024-01-04T00:00:00, 6.0)
 TimeTick(2024-01-07T00:00:00, 9.0)
 TimeTick(2024-01-09T00:00:00, 12.0)

julia> ta_rolling(sum, t_array, 3; observations = 1)
5-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, 1.0)
 TimeTick(2024-01-03T00:00:00, 3.0)
 TimeTick(2024-01-04T00:00:00, 6.0)
 TimeTick(2024-01-07T00:00:00, 9.0)
 TimeTick(2024-01-09T00:00:00, 12.0)

```
