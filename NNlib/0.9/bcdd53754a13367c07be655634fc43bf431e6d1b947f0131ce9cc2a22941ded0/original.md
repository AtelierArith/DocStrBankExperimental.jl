```
batched_transpose(A::AbstractArray{T,3})
batched_adjoint(A)
```

Equivalent to applying `transpose` or `adjoint` to each matrix `A[:,:,k]`.

These exist to control how `batched_mul` behaves, as it operates on such matrix slices of an array with `ndims(A)==3`.

`PermutedDimsArray(A, (2,1,3))` is equivalent to `batched_transpose(A)`, and is also understood by `batched_mul` (and more widely supported elsewhere).

```
BatchedTranspose{T, S} <: AbstractBatchedMatrix{T, 3}
BatchedAdjoint{T, S}
```

Lazy wrappers analogous to `Transpose` and `Adjoint`, returned by `batched_transpose` etc.
