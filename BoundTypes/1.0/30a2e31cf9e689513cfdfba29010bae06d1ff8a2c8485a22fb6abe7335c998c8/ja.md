```
TimeAfterNow{T<:TimeType} <: BoundTime{T}
TimeAfterNow{T}(x::TimeType)
```

現在の時間を超えなければならない型 `T` の値 `x` に対する時間制約です。

## 例

```julia-repl
julia> using Dates

julia> TimeAfterNow{DateTime}(DateTime(2030))
2030-01-01T00:00:00

julia> TimeAfterNow{DateTime}(DateTime(2020))
ERROR: ConstraintError: constraints of type TimeAfterNow violated.
Wrong value: 2020-01-01T00:00:00 must exceed 2024-05-03T11:25:26.689.
[...]
```
