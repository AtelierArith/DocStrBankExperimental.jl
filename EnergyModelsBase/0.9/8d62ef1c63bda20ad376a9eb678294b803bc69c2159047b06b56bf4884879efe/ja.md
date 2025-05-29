```
emission_price(modeltype::EnergyModel)
emission_price(modeltype, p::ResourceEmit)
emission_price(modeltype, p::ResourceEmit, t_inv::TS.TimePeriod)
```

エネルギーモデル `model` の排出価格を、各 [`ResourceEmit`](@ref) の `TimeProfile` を持つ辞書として返します。また、[`ResourceEmit`](@ref) `p` の `TimeProfile` と、[`ResourceEmit`](@ref) `p` の運用期間 `t` に対しても返します。
