```
TimeBefore{T<:TimeType,V} <: BoundTime{T}
TimeBefore{T,V}(x::TimeType)
```

値 `x` の型 `T` に対する時間制約であり、これは時間 `V` よりも前でなければなりません。

## 例

```jldoctest
julia> using Dates

julia> TimeBefore{DateTime,DateTime(2023)}(DateTime(2022))
2022-01-01T00:00:00

julia> TimeBefore{DateTime,DateTime(2023)}(DateTime(2024))
ERROR: ConstraintError: constraints of type TimeBefore violated.
Wrong value: 2024-01-01T00:00:00 must precede 2023-01-01T00:00:00.
[...]
```
