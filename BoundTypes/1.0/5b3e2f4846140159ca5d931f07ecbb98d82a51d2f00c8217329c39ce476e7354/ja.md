```
NumberOdd{T<:Number} <: BoundNumber{T}
NumberOdd{T}(x::Number)
```

値 `x` が型 `T` の奇数であることを保証する数値制約です。

## 例

```jldoctest
julia> NumberOdd{Float64}(5.0)
5.0

julia> NumberOdd{Float64}(4.0)
ERROR: ConstraintError: constraints of type NumberOdd violated.
Wrong value: 4.0 must be odd.
[...]
```
