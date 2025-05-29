```julia
struct MaskedReLU{T<:Real} <: MIPVerify.Layer
```

マスクされたReLU活性化を表し、`mask`が各出力にReLUがどのように適用されるかを制御します。

`p(x)`は、`p`が`MaskedReLU`のインスタンスであるとき、[`masked_relu(x, p.mask)`](@ref)の短縮形です。

## フィールド:

  * `mask`
  * `tightening_algorithm`
