```
TimeCustomBound{T<:TimeType,B} <: BoundTime{T}
TimeCustomBound{T,B}(x::TimeType)
```

カスタム関数 `B` を使用して型 `T` の値 `x` に対する時間制約。関数 `B` はオブジェクト `x` のみを受け入れ、`true` または `false` を返す必要があります（またはカスタム [`ConstraintError`](@ref) をスローします）。

## 例

```julia-repl
julia> using Dates

julia> TimeCustomBound{DateTime,isleapyear}(DateTime(2024))
2024-01-01T00:00:00

julia> TimeCustomBound{DateTime,isleapyear}(DateTime(2023))
ERROR: ConstraintError: constraints of type TimeCustomBound violated.
Wrong value: Custom constraint 'isleapyear' violated for value "2023-01-01T00:00:00" of type DateTime.
[...]
```
