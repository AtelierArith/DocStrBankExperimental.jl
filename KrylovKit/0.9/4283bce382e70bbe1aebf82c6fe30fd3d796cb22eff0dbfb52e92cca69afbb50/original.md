```
CG(; maxiter=KrylovDefaults.maxiter[], tol=KrylovDefaults.tol[], verbosity=KrylovDefaults.verbosity[])
```

Construct an instance of the conjugate gradient algorithm with specified parameters, which can be passed to `linsolve` in order to iteratively solve a linear system with a positive definite (and thus symmetric or hermitian) coefficient matrix or operator. The `CG` method will search for the optimal `x` in a Krylov subspace of maximal size `maxiter`, or stop when `norm(A*x - b) < tol`. The default verbosity level `verbosity` amounts to printing warnings upon lack of convergence.

See also: [`linsolve`](@ref), [`MINRES`](@ref), [`GMRES`](@ref), [`BiCG`](@ref), [`LSMR`](@ref), [`BiCGStab`](@ref)
