```
NumberNonNegative{T<:Number} <: BoundNumber{T}
NumberNonNegative{T}(x::Number)
```

値 `x` が型 `T` のために `x ≥ 0` を強制する数値制約です。

## 例

```jldoctest
julia> NumberNonNegative{Float64}(10.0)
10.0

julia> NumberNonNegative{Float64}(-10.0)
ERROR: ConstraintError: constraints of type NumberNonNegative violated.
Wrong value: -10.0 must be a positive or zero (x ≥ 0).
[...]
```
