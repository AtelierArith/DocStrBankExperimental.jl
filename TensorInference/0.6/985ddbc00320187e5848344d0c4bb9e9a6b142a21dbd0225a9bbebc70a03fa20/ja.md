```julia
random_matrix_product_uai(
    ::Type{T},
    n::Int64,
    chi::Int64
) -> TensorInference.UAIModel
random_matrix_product_uai(
    ::Type{T},
    n::Int64,
    chi::Int64,
    d::Int64
) -> TensorInference.UAIModel

```

行列積状態（MPS）を表すランダムなUAIModelを生成します。[`random_matrix_product_state`](@ref)と似ていますが、UAIModelを直接返します。
