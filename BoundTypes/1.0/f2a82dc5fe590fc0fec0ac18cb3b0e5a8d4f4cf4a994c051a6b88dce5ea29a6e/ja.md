```
NumberInterval{T<:Number,A,L,R,B} <: BoundNumber{T}
NumberInterval{T,A,L,R,B}(x::Number)
```

値 `x` の型 `T` に対する数値制約であり、`A` と `B` の間の区間に属します。パラメータ `L` と `R` は、区間の境界が含まれるかどうかを決定する比較関数（例：`<` または `<=`）です。

## 例

```jldoctest
julia> NumberInterval{Float64,5,<,<=,10}(7.0)
7.0

julia> NumberInterval{Float64,5,<,<=,10}(10.0)
10.0

julia> NumberInterval{Float64,5,<,<=,10}(15.0)
ERROR: ConstraintError: constraints of type NumberInterval violated.
Wrong value: 15.0 must be in interval between 5 and 10.
[...]
```
