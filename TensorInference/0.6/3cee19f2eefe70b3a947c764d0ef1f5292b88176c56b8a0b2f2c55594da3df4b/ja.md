```julia
log_probability(
    tn::TensorInference.TensorNetworkModel;
    usecuda
) -> AbstractArray

```

対数確率（または分配関数）を評価します。これは、オーバーフローする可能性が低い[`probability`](@ref)のログ版です。
