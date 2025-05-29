```julia
log_probability(
    tn::TensorInference.TensorNetworkModel,
    config::Union{Dict, AbstractVector}
) -> Real

```

Evaluate the log probability (or partition function) of `config`.
