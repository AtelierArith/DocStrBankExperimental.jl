```
NumberNonPositive{T<:Number} <: BoundNumber{T}
NumberNonPositive{T}(x::Number)
```

値 `x` が型 `T` の場合に `x ≤ 0` を強制する数値制約です。

## 例

```jldoctest
julia> NumberNonPositive{Float64}(-10.0)
-10.0

julia> NumberNonPositive{Float64}(10.0)
ERROR: ConstraintError: constraints of type NumberNonPositive violated.
Wrong value: number 10.0 must be a negative or zero (x ≤ 0).
[...]
```
