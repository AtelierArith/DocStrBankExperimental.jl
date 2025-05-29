```
ta_backward_fill([, pattern::Function], t_array::TimeArray) -> TimeArray
```

`pattern` に一致する要素が `t_array` の最も近い前の非パターン値に置き換えられた配列を返します。デフォルトでは `pattern` は `isnan` 関数です。

## 例

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
