```
NumberNegative{T<:Number} <: BoundNumber{T}
NumberNegative{T}(x::Number)
```

値 `x` が型 `T` の場合に `x < 0` を強制する数値制約です。

## 例

```jldoctest
julia> NumberNegative{Float64}(-10.0)
-10.0

julia> NumberNegative{Float64}(10.0)
ERROR: ConstraintError: constraints of type NumberNegative violated.
Wrong value: 10.0 must be a negative (x < 0).
[...]
```
