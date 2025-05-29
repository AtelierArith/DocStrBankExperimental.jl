```
batched_mul(A::Array{T,3}, B::Matrix)
batched_mul(A::Matrix, B::Array{T,3})
A ⊠ B
```

これは常に行列-行列の乗算ですが、`A`または`B`のいずれかがバッチインデックスを欠いている可能性があります。

  * `B`が行列の場合、結果は`C[:,:,k] == A[:,:,k] * B[:,:]`となります（すべての`k`について）。
  * `A`が行列の場合、`C[:,:,k] == A[:,:] * B[:,:,k]`となります。これは、例えば`A ⊡ B`を使用してTensorCore.jlで呼び出すことによっても行うことができますが、ここでは`gemm`の代わりに`batched_gemm`を使用して実装されています。

```jldoctest
julia> randn(16,8,32) ⊠ randn(8,4) |> size
(16, 4, 32)

julia> randn(16,8,32) ⊠ randn(8,4,1) |> size  # equivalent
(16, 4, 32)

julia> randn(16,8) ⊠ randn(8,4,32) |> size
(16, 4, 32)
```

`B`をベクトルのバッチとして考慮するために`batched_vec`も参照してください。`A[:,:,k] * B[:,k]`。
