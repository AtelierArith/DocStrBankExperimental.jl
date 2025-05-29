```
@einsum tns[idxs...] <<op>>= ex...
```

Construct an einsum expression that computes the result of applying `op` to the tensor `tns` with the indices `idxs` and the tensors in the expression `ex`. The result is stored in the variable `tns`.

`ex` may be any pointwise expression consisting of function calls and tensor references of the form `tns[idxs...]`, where `tns` and `idxs` are symbols.

The `<<op>>` operator can be any binary operator that is defined on the element type of the expression `ex`.

The einsum will evaluate the pointwise expression `tns[idxs...] <<op>>= ex...` over all combinations of index values in `tns` and the tensors in `ex`.

Here are a few examples:

```
@einsum C[i, j] += A[i, k] * B[k, j]
@einsum C[i, j, k] += A[i, j] * B[j, k]
@einsum D[i, k] += X[i, j] * Y[j, k]
@einsum J[i, j] = H[i, j] * I[i, j]
@einsum N[i, j] = K[i, k] * L[k, j] - M[i, j]
@einsum R[i, j] <<max>>= P[i, k] + Q[k, j]
@einsum x[i] = A[i, j] * x[j]
```
