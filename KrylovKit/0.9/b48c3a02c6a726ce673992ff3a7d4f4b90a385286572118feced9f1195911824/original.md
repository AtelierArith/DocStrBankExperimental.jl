```
GMRES(; krylovdim=KrylovDefaults.krylovdim[],
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[], 
        orth::Orthogonalizer=KrylovDefaults.orth,
        verbosity=KrylovDefaults.verbosity[])
```

Construct an instance of the GMRES algorithm with specified parameters, which can be passed to `linsolve` in order to iteratively solve a linear system. The `GMRES` method will search for the optimal `x` in a Krylov subspace of maximal size `krylovdim`, and repeat this process for at most `maxiter` times, or stop when `norm(A*x - b) < tol`. In building the Krylov subspace, `GMRES` will use the orthogonalizer `orth`. The default verbosity level `verbosity` amounts to printing warnings upon lack of convergence.

Note that in the traditional nomenclature of `GMRES`, the parameter `krylovdim` is referred to as the restart parameter, and `maxiter` is the number of outer iterations, i.e. restart cycles. The total iteration count, i.e. the number of expansion steps, is roughly `krylovdim` times the number of iterations.

See also: [`linsolve`](@ref), [`BiCG`](@ref), [`BiCGStab`](@ref), [`CG`](@ref), [`LSMR`](@ref), [`MINRES`](@ref)
