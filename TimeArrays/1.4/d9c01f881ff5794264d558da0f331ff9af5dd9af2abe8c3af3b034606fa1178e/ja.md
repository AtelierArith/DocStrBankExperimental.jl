```
ta_linear_fill([, pattern::Function], t_array::TimeArray) -> TimeArray
```

`pattern` に一致する要素が `t_array` の最近接の非パターン値の間で線形補間されて置き換えられた配列を返します。デフォルトでは `pattern` は `isnan` 関数です。

## 例

```jldoctest
julia> using Dates

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-01-02"), 2.0),
           TimeTick(DateTime("2024-01-04"), NaN),
           TimeTick(DateTime("2024-01-06"), NaN),
           TimeTick(DateTime("2024-01-08"), 8.0),
       ]);

julia> ta_linear_fill(t_array)
4-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-02T00:00:00, 2.0)
 TimeTick(2024-01-04T00:00:00, 4.0)
 TimeTick(2024-01-06T00:00:00, 6.0)
 TimeTick(2024-01-08T00:00:00, 8.0)
```
