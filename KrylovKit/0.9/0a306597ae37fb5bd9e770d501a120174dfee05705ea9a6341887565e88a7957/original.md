```
Lanczos(; krylovdim=KrylovDefaults.krylovdim[],
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[],
        orth=KrylovDefaults.orth,
        eager=false,
        verbosity=KrylovDefaults.verbosity[])
```

Represents the Lanczos algorithm for building the Krylov subspace; assumes the linear operator is real symmetric or complex Hermitian. Can be used in `eigsolve` and `exponentiate`. The corresponding algorithms will build a Krylov subspace of size at most `krylovdim`, which will be repeated at most `maxiter` times and will stop when the norm of the residual of the Lanczos factorization is smaller than `tol`. The orthogonalizer `orth` will be used to orthogonalize the different Krylov vectors. Eager mode, as selected by `eager=true`, means that the algorithm that uses this Lanczos process (e.g. `eigsolve`) can try to finish its computation before the total Krylov subspace of dimension `krylovdim` is constructed. The default verbosity level `verbosity` amounts to printing warnings upon lack of convergence.

Use `Arnoldi` for non-symmetric or non-Hermitian linear operators.

See also: `factorize`, `eigsolve`, `exponentiate`, `Arnoldi`, `Orthogonalizer`
