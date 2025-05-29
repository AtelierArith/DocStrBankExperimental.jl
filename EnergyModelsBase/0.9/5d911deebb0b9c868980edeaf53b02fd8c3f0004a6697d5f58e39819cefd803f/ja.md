```
emission_limit(modeltype::EnergyModel)
emission_limit(modeltype, p::ResourceEmit)
emission_limit(modeltype, p::ResourceEmit, t_inv::TS.AbstractStrategicPeriod)
```

エネルギーモデル `model` の排出制限を、各 [`ResourceEmit`](@ref) の `TimeProfile` を持つ辞書として返します。`ResourceEmit`(@ref) `p` の `TimeProfile` と、戦略的期間 `t_inv` における [`ResourceEmit`](@ref) `p` の `TimeProfile` も返します。
