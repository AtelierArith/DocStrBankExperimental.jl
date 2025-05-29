```
NumberGreater{T<:Number,V} <: BoundNumber{T}
NumberGreater{T,V}(x::Number)
```

値 `x` が型 `T` のために `x > V` を強制する数値制約です。

## 例

```jldoctest
julia> NumberGreater{Float64,10.0}(20.0)
20.0

julia> NumberGreater{Float64,10.0}(5.0)
ERROR: ConstraintError: constraints of type NumberGreater violated.
Wrong value: 5.0 must be greater than 10.0.
[...]
```
