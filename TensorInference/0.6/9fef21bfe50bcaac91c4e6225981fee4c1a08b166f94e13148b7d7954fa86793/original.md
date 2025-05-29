```julia
BeliefPropgation(
    uai::TensorInference.UAIModel{T, FT} where FT<:(TensorInference.Factor{T})
) -> TensorInference.BeliefPropgation

```

Construct a belief propagation object from a [`UAIModel`](@ref).
