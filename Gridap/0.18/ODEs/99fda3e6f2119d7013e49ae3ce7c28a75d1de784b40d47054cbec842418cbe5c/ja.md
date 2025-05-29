```
struct TransientTrialFESpace <: SingleFieldFESpace end
```

`TrialFESpace`の一時的なバージョン：ディリクレ境界条件は時間依存であることが許可されています。

# 必須

  * [`allocate_space(space)`](@ref)
  * [`evaluate!(space, t)`](@ref)
  * [`evaluate(space, t)`](@ref)
  * [`time_derivative(space)`](@ref)

# オプション

  * [`evaluate(space, t::Real)`](@ref)
