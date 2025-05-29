```julia
partialschur!(A, arnoldi; start_from, initialize, nev, which, tol, mindim, maxdim, restarts) → PartialSchur, History
```

This is a variant of [`partialschur`](@ref) that operates on a pre-allocated [`ArnoldiWorkspace`](@ref) instance. This is useful in the following cases:

1. To provide an initial partial Schur decomposition. In that case, set `start_from` to the number of Schur vectors, and `partialschur` will continue from there. Notice that if you have only one Schur vector, it can be simpler to pass it as `v1` instead.
2. To provide a custom array type for the basis of the Krylov subspace, the Hessenberg matrix, and some temporaries.
3. To avoid allocations when calling `partialschur` repeatedly.

You can also provide the initial vector that induces the Krylov subspace in the first column arnoldi.V[:, 1]. If you do that, set `initialize` explicitly to `false`.

Upon return, note that the PartialSchur struct will contain views of arnoldi.V and arnoldi.H, no copies are made.
