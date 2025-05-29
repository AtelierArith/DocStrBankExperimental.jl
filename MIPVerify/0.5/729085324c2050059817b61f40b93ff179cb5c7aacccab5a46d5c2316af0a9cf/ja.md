```julia
struct Flatten{T<:Integer} <: MIPVerify.Layer
```

フラット化操作を表します。

`p(x)` は、`p` が `Flatten` のインスタンスであるとき、[`permute_and_flatten(x, p.perm)`](@ref) の短縮形です。

## フィールド:

  * `n_dim`
  * `perm`
