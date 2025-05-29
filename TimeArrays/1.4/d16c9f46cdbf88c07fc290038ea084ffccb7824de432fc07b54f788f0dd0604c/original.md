```
ta_rolling(f::Function, t_array::TimeArray, p::Period; kw...) -> TimeArray
```

Applies function `f` in a sliding window with window period `p` to the elements of `t_array`. Function `f` must accept a vector with elements of type `V` as input and return a new value, which will be assigned to the corresponding timestamp of each window.

Function signature:

```julia
f(x::AbstractVector{V})::Any = ...
```

## Keyword arguments

  * `observations::Integer = 1`: Number of observations in the rolling window to calculate the value (otherwise `NaN`).

!!! note
    The first elements of the `t_array` during period `p` will always be replaced by `NaN` values (not enough elements in the window).


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

julia> ta_rolling(sum, t_array, Day(3))
5-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, NaN)
 TimeTick(2024-01-03T00:00:00, 3.0)
 TimeTick(2024-01-04T00:00:00, 5.0)
 TimeTick(2024-01-07T00:00:00, 4.0)
 TimeTick(2024-01-09T00:00:00, 9.0)

julia> ta_rolling(sum, t_array, Day(3); observations = 2)
5-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, NaN)
 TimeTick(2024-01-03T00:00:00, 3.0)
 TimeTick(2024-01-04T00:00:00, 5.0)
 TimeTick(2024-01-07T00:00:00, NaN)
 TimeTick(2024-01-09T00:00:00, 9.0)
```
