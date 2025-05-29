```
batched_mul!(C, A, B) -> C
batched_mul!(C, A, B, α=1, β=0)
```

インプレースバッチ行列乗算であり、すべての `k` に対して `mul!(C[:,:,k], A[:,:,k], B[:,:,k], α, β)` に相当します。もし `size(B,3) == 1` であれば、すべてのバッチは `B[:,:,1]` を使用します。

これは可能な限り `batched_gemm!` を呼び出します。実数配列の場合、`X ∈ [A,B,C]` に対して、`stride(X,1)==1` または `stride(X,2)==1` のいずれかが成り立つ必要があります。後者は `batched_transpose` や例えば `PermutedDimsArray(::Array, (3,1,2))` によって引き起こされることがあります。`batched_mul` とは異なり、これは決してコピーを作成しません。

複素数配列の場合、`batched_adjoint` によって作成されたラッパーは、最外層でなければ認識されません。この場合、BLAS によって受け入れられるストライドはより制限されており、`stride(C,1)==1` であれば、`stride(AorB::BatchedAdjoint,2) == 1` のみが受け入れられます。
