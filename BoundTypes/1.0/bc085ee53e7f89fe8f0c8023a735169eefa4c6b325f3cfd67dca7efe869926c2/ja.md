```
TimePeriodAfterNow{T<:TimeType,P} <: BoundTime{T}
TimePeriodAfterNow{T,P}(x::TimeType)
```

現在の時間を超える必要がある値 `x` のための時間制約で、型は `T` であり、期間は `P` です。

## 例

```julia-repl
julia> using Dates

julia> TimePeriodAfterNow{DateTime,Year(10)}(DateTime(2030))
2030-01-01T00:00:00

julia> TimePeriodAfterNow{DateTime,Year(10)}(DateTime(2050))
ERROR: ConstraintError: constraints of type TimePeriodAfterNow violated.
Wrong value: 2050-01-01T00:00:00 must be in interval between 2024-05-03T11:29:14 and 2034-05-03T11:29:14.
[...]
```
