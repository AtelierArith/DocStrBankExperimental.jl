```
TimeAfterOrEqual{T<:TimeType,V} <: BoundTime{T}
TimeAfterOrEqual{T,V}(x::TimeType)
```

値 `x` の型 `T` に対する時間制約であり、時間 `V` を超えるか等しい必要があります。

## 例

```jldoctest
julia> using Dates

julia> TimeAfterOrEqual{DateTime,DateTime(2023)}(DateTime(2024))
2024-01-01T00:00:00

julia> TimeAfterOrEqual{DateTime,DateTime(2023)}(DateTime(2023))
2023-01-01T00:00:00

julia> TimeAfterOrEqual{DateTime,DateTime(2023)}(DateTime(2022))
ERROR: ConstraintError: constraints of type TimeAfterOrEqual violated.
Wrong value: 2022-01-01T00:00:00 must exceed or be equal to 2023-01-01T00:00:00.
[...]
```
