```
TimeInterval{T<:TimeType,A,L,R,B} <: BoundTime{T}
TimeInterval{T,A,L,R,B}(x::TimeType)
```

値 `x` が型 `T` のもので、時間 `A` と `B` の間の区間に属するための時間制約。パラメータ `L` と `R` は、区間の境界が含まれるかどうかを決定する比較関数（例：`<` または `<=`）です。

## 例

```jldoctest
julia> using Dates

julia> TimeInterval{DateTime,DateTime(2023),<,<,DateTime(2025)}(DateTime(2024))
2024-01-01T00:00:00

julia> TimeInterval{DateTime,DateTime(2023),<,<=,DateTime(2025)}(DateTime(2025))
2025-01-01T00:00:00

julia> TimeInterval{DateTime,DateTime(2023),<,<,DateTime(2025)}(DateTime(2025))
ERROR: ConstraintError: constraints of type TimeInterval violated.
Wrong value: 2025-01-01T00:00:00 must be in interval between 2023-01-01T00:00:00 and 2025-01-01T00:00:00.
[...]
```
