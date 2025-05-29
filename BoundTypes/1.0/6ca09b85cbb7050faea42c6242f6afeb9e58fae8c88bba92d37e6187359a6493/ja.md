```
TimeAfter{T<:TimeType,V} <: BoundTime{T}
TimeAfter{T,V}(x::TimeType)
```

値 `x` の型 `T` に対する時間制約であり、これは時間 `V` を超えなければなりません。

## 例

```jldoctest
julia> using Dates

julia> TimeAfter{DateTime,DateTime(2023)}(DateTime(2024))
2024-01-01T00:00:00

julia> TimeAfter{DateTime,DateTime(2023)}(DateTime(2022))
ERROR: ConstraintError: constraints of type TimeAfter violated.
Wrong value: 2022-01-01T00:00:00 must exceed 2023-01-01T00:00:00.
[...]
```
