```julia
log_probability(
    tn::TensorInference.TensorNetworkModel;
    usecuda
) -> AbstractArray

```

Evaluate the log probability (or partition function). It is the logged version of [`probability`](@ref), which is less likely to overflow.
