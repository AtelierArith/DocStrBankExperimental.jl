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

Generate a random UAIModel that represents a matrix product state (MPS). Similar to [`random_matrix_product_state`](@ref), but returns the UAIModel directly.
