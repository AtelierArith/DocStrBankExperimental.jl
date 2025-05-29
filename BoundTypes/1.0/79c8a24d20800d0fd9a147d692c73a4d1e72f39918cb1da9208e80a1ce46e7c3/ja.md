```
NumberLess{T<:Number,V} <: BoundNumber{T}
NumberLess{T,V}(x::Number)
```

値 `x` が型 `T` の場合に `x < V` を強制する数値制約です。

## 例

```jldoctest
julia> NumberLess{Float64,10.0}(5.0)
5.0

julia> NumberLess{Float64,10.0}(20.0)
ERROR: ConstraintError: constraints of type NumberLess violated.
Wrong value: 20.0 must be less than 10.0.
[...]
```
