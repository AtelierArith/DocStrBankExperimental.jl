```
NumberGreaterOrEqual{T<:Number,V} <: BoundNumber{T}
NumberGreaterOrEqual{T,V}(x::Number)
```

値 `x` が型 `T` の場合に `x ≥ V` を強制する数値制約です。

## 例

```jldoctest
julia> NumberGreaterOrEqual{Float64,10.0}(20.0)
20.0

julia> NumberGreaterOrEqual{Float64,10.0}(5.0)
ERROR: ConstraintError: constraints of type NumberGreaterOrEqual violated.
Wrong value: 5.0 must be greater or equal than 10.0.
[...]
```
