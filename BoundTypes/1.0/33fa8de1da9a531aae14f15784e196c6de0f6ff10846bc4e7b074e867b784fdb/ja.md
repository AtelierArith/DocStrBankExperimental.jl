```
NumberPositive{T<:Number} <: BoundNumber{T}
NumberPositive{T}(x::Number)
```

値 `x` の型 `T` に対して `x > 0` を強制する数値制約です。

## 例

```jldoctest
julia> NumberPositive{Float64}(10.0)
10.0

julia> NumberPositive{Float64}(-10.0)
ERROR: ConstraintError: constraints of type NumberPositive violated.
Wrong value: number -10.0 must be a positive (x > 0).
[...]
```
