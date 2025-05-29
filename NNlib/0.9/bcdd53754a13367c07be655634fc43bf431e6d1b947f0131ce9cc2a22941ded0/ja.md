```
batched_transpose(A::AbstractArray{T,3})
batched_adjoint(A)
```

各行列 `A[:,:,k]` に `transpose` または `adjoint` を適用することと同等です。

これらは、`ndims(A)==3` の配列のそのような行列スライスで動作する `batched_mul` の動作を制御するために存在します。

`PermutedDimsArray(A, (2,1,3))` は `batched_transpose(A)` と同等であり、`batched_mul` によっても理解され（他の場所でもより広くサポートされています）、

```
BatchedTranspose{T, S} <: AbstractBatchedMatrix{T, 3}
BatchedAdjoint{T, S}
```

`batched_transpose` などによって返される `Transpose` および `Adjoint` に類似した遅延ラッパーです。
