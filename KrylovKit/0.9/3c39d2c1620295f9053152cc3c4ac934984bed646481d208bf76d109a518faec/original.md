```
GKL(; krylovdim=KrylovDefaults.krylovdim[],
    maxiter=KrylovDefaults.maxiter[],
    tol=KrylovDefaults.tol[],
    orth=KrylovDefaults.orth,
    eager=false,
    verbosity=KrylovDefaults.verbosity[])
```

Represents the Golub-Kahan-Lanczos bidiagonalization algorithm for sequentially building a Krylov-like factorization of a general matrix or linear operator with a bidiagonal reduced matrix. Can be used in `svdsolve`. The corresponding algorithm builds a Krylov subspace of size at most `krylovdim`, which will be repeated at most `maxiter` times and will stop when the norm of the residual of the Arnoldi factorization is smaller than `tol`. The orthogonalizer `orth` will be used to orthogonalize the different Krylov vectors. The default verbosity level `verbosity` amounts to printing warnings upon lack of convergence.

See also: [`svdsolve`](@ref), [`Orthogonalizer`](@ref)
