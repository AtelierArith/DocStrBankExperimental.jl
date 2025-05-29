```
ta_mergewith(f, l_array::TimeArray, r_array::TimeArray; kw...) -> TimeArray
```

Creates a new TimeArray object by applying a binary function `f` on elements of `left` and `right` TimeArrays. TimeArrays uses the following rules to establish corresponding elements:

  * An element of the first array is matched to the nearest smaller or equal element of the second array.
  * If there is no such element in the second array, then the resulting element will be `NaN`.

## Keyword arguments

  * `l_merge::Bool = true`: Use `left` timestamps in resulting TimeArray.
  * `r_merge::Bool = true`: Use `right` timestamps in resulting TimeArray.
  * `padding::Bool = true`: Preserve first timestamps with `NaN` values.

## Examples

```jldoctest
julia> using Dates

julia> t_left = TimeArray([
           TimeTick(DateTime("2024-01-02"), 0.2),
           TimeTick(DateTime("2024-01-05"), 0.5),
       ]);

julia> t_right = TimeArray([
           TimeTick(DateTime("2024-01-01"), 1.0),
           TimeTick(DateTime("2024-01-05"), 5.0),
           TimeTick(DateTime("2024-01-07"), 7.0),
       ]);

julia> ta_mergewith(+, t_left, t_right)
4-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, NaN)
 TimeTick(2024-01-02T00:00:00, 1.2)
 TimeTick(2024-01-05T00:00:00, 5.5)
 TimeTick(2024-01-07T00:00:00, 7.5)

julia> ta_mergewith(-, t_left, t_right; l_merge = false)
3-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, NaN)
 TimeTick(2024-01-05T00:00:00, -4.5)
 TimeTick(2024-01-07T00:00:00, -6.5)

julia> ta_mergewith(*, t_left, t_right, r_merge = false, padding = false)
2-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-02T00:00:00, 0.2)
 TimeTick(2024-01-05T00:00:00, 2.5)
```
