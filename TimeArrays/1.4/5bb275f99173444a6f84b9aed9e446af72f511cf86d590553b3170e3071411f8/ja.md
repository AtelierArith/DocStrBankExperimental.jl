```
ta_merge(f::Function, t_array::TimeArray, value) -> TimeArray
ta_merge(f::Function, value, t_array::TimeArray) -> TimeArray
```

`f`と`t_array`の要素に`value`を適用することで新しいTimeArrayを作成します。

## 例

```jldoctest
julia> using Dates

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-01-03"), 2.0),
           TimeTick(DateTime("2024-01-04"), 3.0),
           TimeTick(DateTime("2024-01-08"), 6.0),
       ]);

julia> ta_merge(+, t_array, 2.0)
3-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-03T00:00:00, 4.0)
 TimeTick(2024-01-04T00:00:00, 5.0)
 TimeTick(2024-01-08T00:00:00, 8.0)

julia> ta_merge(/, 18.0, t_array)
3-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-03T00:00:00, 9.0)
 TimeTick(2024-01-04T00:00:00, 6.0)
 TimeTick(2024-01-08T00:00:00, 3.0)
```
