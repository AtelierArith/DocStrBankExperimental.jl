```julia
random_tensor_train_uai(
    ::Type{T},
    n::Int64,
    chi::Int64;
    ...
) -> TensorInference.UAIModel
random_tensor_train_uai(
    ::Type{T},
    n::Int64,
    chi::Int64,
    d::Int64;
    periodic
) -> TensorInference.UAIModel

```

Tensor train (TT) is a tensor network model that is widely used in quantum many-body physics. This model is different from the matrix product state (MPS) in that it does not have an extra copy for representing the bra state.
