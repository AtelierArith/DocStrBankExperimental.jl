```
Arnoldi(; krylovdim=KrylovDefaults.krylovdim[],
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[],
        orth=KrylovDefaults.orth,
        eager=false,
        verbosity=KrylovDefaults.verbosity[])
```

Represents the Arnoldi algorithm for building the Krylov subspace for a general matrix or linear operator. Can be used in `eigsolve` and `exponentiate`. The corresponding algorithms will build a Krylov subspace of size at most `krylovdim`, which will be repeated at most `maxiter` times and will stop when the norm of the residual of the Arnoldi factorization is smaller than `tol`. The orthogonalizer `orth` will be used to orthogonalize the different Krylov vectors. Eager mode, as selected by `eager=true`, means that the algorithm that uses this Arnoldi process (e.g. `eigsolve`) can try to finish its computation before the total Krylov subspace of dimension `krylovdim` is constructed. The default verbosity level `verbosity` amounts to printing warnings upon lack of convergence.

Use `Lanczos` for real symmetric or complex Hermitian linear operators.

See also: [`eigsolve`](@ref), [`exponentiate`](@ref), [`Lanczos`](@ref), [`Orthogonalizer`](@ref)
