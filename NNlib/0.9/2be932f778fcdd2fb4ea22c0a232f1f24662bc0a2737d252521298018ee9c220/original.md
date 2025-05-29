```
batched_vec(A::Array{T,3}, B::Matrix)
batched_vec(A::Array{T,3}, b::Vector)
```

Batched matrix-vector multiplication: the result has `C[:,:,k] == A[:,:,k] * B[:,k]` for all `k`, or else `C[:,:,k] == A[:,:,k] * b` for `b::Vector`.

With the same argument types, `batched_mul(A, B)` would regard `B` as a fixed matrix, not a batch of vectors. Both reshape and then call `batched_mul(::Array{T,3}, ::Array{T,3})`.

```jldoctest
julia> A, B, b = randn(16,8,32), randn(8,32), randn(8);

julia> batched_vec(A,B) |> size
(16, 32)

julia> batched_vec(A,b) |> size
(16, 32)
```
