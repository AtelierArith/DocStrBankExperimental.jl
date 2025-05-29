```
TimeBeforeNow{T<:TimeType} <: BoundTime{T}
TimeBeforeNow{T}(x::TimeType)
```

現在の時間より前でなければならない型 `T` の値 `x` に対する時間制約です。

## 例

```julia-repl
julia> using Dates

julia> TimeBeforeNow{DateTime}(DateTime(2020))
2020-01-01T00:00:00

julia> TimeBeforeNow{DateTime}(DateTime(2030))
ERROR: ConstraintError: constraints of type TimeBeforeNow violated.
Wrong value: 2030-01-01T00:00:00 must precede 2024-05-03T11:36:37.848.
[...]
```
