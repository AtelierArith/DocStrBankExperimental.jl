```julia
BeliefPropgation(
    uai::TensorInference.UAIModel{T, FT} where FT<:(TensorInference.Factor{T})
) -> TensorInference.BeliefPropgation

```

[`UAIModel`](@ref) から信念伝播オブジェクトを構築します。
