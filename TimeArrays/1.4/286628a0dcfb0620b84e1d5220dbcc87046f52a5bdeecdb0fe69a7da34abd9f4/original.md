```
ta_resample(f::Function, t_array::TimeArray{T,V}, period::PeriodLike; kw...) -> TimeArray
```

Brings the values of `t_array` to a new time grid with new `period` using the function `f` on intermediate values of the old grid.

Function `f` must accept a vector with elements of type `V` as input and return a new value, which will be assigned to the corresponding timestamp of the each window. If it is impossible to calculate a new value based on the received vector (for example, the vector is empty), then the `NaN` value or an equivalent value (for custom types) must be returned.

## Keyword arguments

  * `origin::ORIGIN_TYPE = ORIGIN_OF_WINDOW`: Start of new grid (Possible values: `ORIGIN_OF_WINDOW`, `START_OF_WINDOW`, `END_OF_WINDOW`).
  * `closed::CLOSED_SIDE = CLOSED_LEFT`: Closed side of the half-open subintervals of new grid (Possible values: `CLOSED_LEFT`, `CLOSED_RIGHT`).
  * `label::LABEL_SIDE = LABEL_LEFT`: Label side of the subintervals of new grid (Possible values: `LABEL_LEFT`, `LABEL_RIGHT`).

For more information see [`resample section`](@ref resample).

## Examples

```jldoctest
julia> t_array = TimeArray{Int64,Int64}([(i, i) for i in 3:13])
11-element TimeArray{Int64, Int64}:
 TimeTick(3, 3)
 TimeTick(4, 4)
 TimeTick(5, 5)
 TimeTick(6, 6)
 TimeTick(7, 7)
 TimeTick(8, 8)
 TimeTick(9, 9)
 TimeTick(10, 10)
 TimeTick(11, 11)
 TimeTick(12, 12)
 TimeTick(13, 13)

julia> ta_resample(sum, t_array, 4, closed = CLOSED_LEFT, label = LABEL_LEFT)
4-element TimeArray{Int64, Int64}:
 TimeTick(0, 3)
 TimeTick(4, 22)
 TimeTick(8, 38)
 TimeTick(12, 25)

julia> ta_resample(sum, t_array, 4, closed = CLOSED_LEFT, label = LABEL_RIGHT)
4-element TimeArray{Int64, Int64}:
 TimeTick(4, 3)
 TimeTick(8, 22)
 TimeTick(12, 38)
 TimeTick(16, 25)

julia> ta_resample(sum, t_array, 4, closed = CLOSED_RIGHT, label = LABEL_LEFT)
4-element TimeArray{Int64, Int64}:
 TimeTick(0, 7)
 TimeTick(4, 26)
 TimeTick(8, 42)
 TimeTick(12, 13)

julia> ta_resample(sum, t_array, 4, closed = CLOSED_RIGHT, label = LABEL_RIGHT)
4-element TimeArray{Int64, Int64}:
 TimeTick(4, 7)
 TimeTick(8, 26)
 TimeTick(12, 42)
 TimeTick(16, 13)
```

```jldoctest
julia> using Dates

julia> t_array = TimeArray{DateTime,Float64}([
           TimeTick(DateTime("2024-01-01"), 1.0),
           TimeTick(DateTime("2024-01-02"), 2.0),
           TimeTick(DateTime("2024-01-03"), 3.0),
           TimeTick(DateTime("2024-01-09"), 4.0),
           TimeTick(DateTime("2024-01-12"), 5.0),
           TimeTick(DateTime("2024-01-13"), 6.0),
           TimeTick(DateTime("2024-01-20"), 7.0),
       ]);

julia> ta_resample(x -> isempty(x) ? NaN : maximum(x), t_array, Day(3))
7-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, 3.0)
 TimeTick(2024-01-04T00:00:00, NaN)
 TimeTick(2024-01-07T00:00:00, 4.0)
 TimeTick(2024-01-10T00:00:00, 5.0)
 TimeTick(2024-01-13T00:00:00, 6.0)
 TimeTick(2024-01-16T00:00:00, NaN)
 TimeTick(2024-01-19T00:00:00, 7.0)
```
