```
ta_forward_fill([, pattern::Function], t_array::TimeArray) -> TimeArray
```

要素が `pattern` に一致する場合、`t_array` 内の次の非パターン値で置き換えられた配列を返します。デフォルトでは `pattern` は `isnan` 関数です。

## 例

```jldoctest
julia> using Dates

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-01-01"), 2.0),
           TimeTick(DateTime("2024-01-03"), NaN),
           TimeTick(DateTime("2024-01-04"), NaN),
           TimeTick(DateTime("2024-01-08"), 7.0),
       ]);

julia> ta_forward_fill(t_array)
4-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, 2.0)
 TimeTick(2024-01-03T00:00:00, 7.0)
 TimeTick(2024-01-04T00:00:00, 7.0)
 TimeTick(2024-01-08T00:00:00, 7.0)
```
