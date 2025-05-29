```julia
log_probability(
    tn::TensorInference.TensorNetworkModel,
    config::Union{Dict, AbstractVector}
) -> Real

```

`config`の対数確率（または分配関数）を評価します。
