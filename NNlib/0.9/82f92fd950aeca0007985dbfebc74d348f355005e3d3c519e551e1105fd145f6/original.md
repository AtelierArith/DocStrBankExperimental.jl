```
batched_mul(A, B) -> C
A ⊠ B  # \boxtimes
```

Batched matrix multiplication. Result has `C[:,:,k...] == A[:,:,k...] * B[:,:,k...]` where `k...` represent  any indices in the last dimensions.

If `ndims(A) == ndims(B) == 3` and `size(B,3) == 1` then instead `C[:,:,k] == A[:,:,k] * B[:,:,1]`, and similarly for `A`.

To transpose each matrix, apply `batched_transpose` to the array, or `batched_adjoint` for conjugate-transpose:

```jldoctest
julia> A, B = randn(2,5,17), randn(5,9,17);

julia> A ⊠ B |> size
(2, 9, 17)

julia> batched_adjoint(A) |> size
(5, 2, 17)

julia> batched_mul(A, batched_adjoint(randn(9,5,17))) |> size
(2, 9, 17)

julia> A ⊠ randn(5,9,1) |> size
(2, 9, 17)

julia> batched_transpose(A) == PermutedDimsArray(A, (2,1,3))
true
```

The equivalent `PermutedDimsArray` may be used in place of `batched_transpose`. Other permutations are also handled by BLAS, provided that the batch index `k` is not the first dimension of the underlying array. Thus `PermutedDimsArray(::Array, (1,3,2))` and `PermutedDimsArray(::Array, (3,1,2))` are fine.

However, `A = PermutedDimsArray(::Array, (3,2,1))` is not acceptable to BLAS, since the batch dimension is the contiguous one: `stride(A,3) == 1`. This will be copied, as doing so is faster than `batched_mul_generic!`.

Both this `copy` and `batched_mul_generic!` produce `@debug` messages, and setting for instance `ENV["JULIA_DEBUG"] = NNlib` will display them.
