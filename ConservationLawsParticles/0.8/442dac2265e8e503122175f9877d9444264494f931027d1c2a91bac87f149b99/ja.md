```
compute_interaction(t, x, interaction, ys[, dens_diff])
```

粒子 `ys` によって `(t, x)` で生成される相互作用を評価します。

`interaction` は `SampledInteraction`、`IntegratedInteraction`、またはこのインターフェースを提供する他の形式の相互作用である可能性があります。

さらに詳しくは [`SampledInteraction`](@ref)、[`IntegratedInteraction`](@ref)、[`sampled_interaction`](@ref)、[`integrated_interaction`](@ref) を参照してください。
