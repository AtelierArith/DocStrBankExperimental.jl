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

テンソル列（TT）は、量子多体物理学で広く使用されているテンソルネットワークモデルです。このモデルは、ブラ状態を表すための追加のコピーを持たない点で、行列積状態（MPS）とは異なります。
