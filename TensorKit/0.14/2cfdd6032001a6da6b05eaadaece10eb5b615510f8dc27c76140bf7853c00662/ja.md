```
Tensor{T, S, N, A<:DenseVector{T}} = TensorMap{T, S, N, 0, A}
```

密なベクトルにデータが格納されているテンソルを表すための[`AbstractTensor`](@ref)の特定のサブタイプです。

`Tensor{T, S, N, A}`は実際には特別なケースの`TensorMap{T, S, N, 0, A}`であり、すなわち非自明な出力空間のみを持つテンソルマップです。
