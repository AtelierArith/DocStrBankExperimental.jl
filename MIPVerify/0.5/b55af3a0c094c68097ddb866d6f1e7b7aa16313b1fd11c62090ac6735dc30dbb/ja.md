```julia
struct Conv2d{T<:Union{Real, JuMP.VariableRef, JuMP.AffExpr}, U<:Union{Real, JuMP.VariableRef, JuMP.AffExpr}, V<:Integer} <: MIPVerify.Layer
```

2次元畳み込み演算を表します。

`p(x)`は、`p`が`Conv2d`のインスタンスであるとき、[`conv2d(x, p)`](@ref)の省略形です。

## フィールド:

  * `filter`
  * `bias`
  * `stride`
  * `padding`
