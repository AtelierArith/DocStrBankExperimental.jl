```
batched_mul!(C, A, B) -> C
batched_mul!(C, A, B, α=1, β=0)
```

In-place batched matrix multiplication, equivalent to `mul!(C[:,:,k], A[:,:,k], B[:,:,k], α, β)` for all `k`. If `size(B,3) == 1` then every batch uses `B[:,:,1]` instead.

This will call `batched_gemm!` whenever possible. For real arrays this means that, for `X ∈ [A,B,C]`, either `stride(X,1)==1` or `stride(X,2)==1`, the latter may be caused by `batched_transpose` or by for instance `PermutedDimsArray(::Array, (3,1,2))`. Unlike `batched_mul` this will never make a copy.

For complex arrays, the wrapper made by `batched_adjoint` must be outermost to be seen. In this case the strided accepted by BLAS are more restricted, if `stride(C,1)==1` then only `stride(AorB::BatchedAdjoint,2) == 1` is accepted.
