```julia
struct Linear{T<:Real, U<:Real} <: MIPVerify.Layer
```

行列の乗算を表します。

`p(x)` は、`p` が `Linear` のインスタンスであるとき、[`matmul(x, p)`](@ref) の省略形です。

## フィールド:

  * `matrix`
  * `bias`
