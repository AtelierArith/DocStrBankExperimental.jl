```julia
struct Pool{N} <: MIPVerify.Layer
```

プーリング操作を表します。

`p(x)` は、`p` が `Pool` のインスタンスであるとき、[`pool(x, p)`](@ref) の短縮形です。

## フィールド:

  * `strides`
  * `pooling_function`
