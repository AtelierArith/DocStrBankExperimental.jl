```
batched_mul(A::Array{T,3}, B::Matrix)
batched_mul(A::Matrix, B::Array{T,3})
A ⊠ B
```

This is always matrix-matrix multiplication, but either `A` or `B` may lack a batch index.

  * When `B` is a matrix, result has `C[:,:,k] == A[:,:,k] * B[:,:]` for all `k`.
  * When `A` is a matrix, then `C[:,:,k] == A[:,:] * B[:,:,k]`. This can also be done by reshaping and calling `*`, for instance `A ⊡ B` using TensorCore.jl, but is implemented here using `batched_gemm` instead of `gemm`.

```jldoctest
julia> randn(16,8,32) ⊠ randn(8,4) |> size
(16, 4, 32)

julia> randn(16,8,32) ⊠ randn(8,4,1) |> size  # equivalent
(16, 4, 32)

julia> randn(16,8) ⊠ randn(8,4,32) |> size
(16, 4, 32)
```

See also `batched_vec` to regard `B` as a batch of vectors, `A[:,:,k] * B[:,k]`.
