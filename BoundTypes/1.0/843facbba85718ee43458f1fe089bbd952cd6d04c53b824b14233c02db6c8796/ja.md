```
NumberEven{T<:Number} <: BoundNumber{T}
NumberEven{T}(x::Number)
```

値 `x` の型 `T` が偶数であることを保証する数値制約です。

## 例

```jldoctest
julia> NumberEven{Float64}(4.0)
4.0

julia> NumberEven{Float64}(5.0)
ERROR: ConstraintError: constraints of type NumberEven violated.
Wrong value: 5.0 must be even.
[...]
```
