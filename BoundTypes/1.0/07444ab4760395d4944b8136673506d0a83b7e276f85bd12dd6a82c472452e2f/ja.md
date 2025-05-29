```
NumberLessOrEqual{T<:Number,V} <: BoundNumber{T}
NumberLessOrEqual{T,V}(x::Number)
```

値 `x` が型 `T` の場合に `x ≤ V` を強制する数値制約です。

## 例

```jldoctest
julia> NumberLessOrEqual{Float64,10.0}(5.0)
5.0

julia> NumberLessOrEqual{Float64,10.0}(20.0)
ERROR: ConstraintError: constraints of type NumberLessOrEqual violated.
Wrong value: 20.0 must be less or equal than 10.0.
[...]
```
