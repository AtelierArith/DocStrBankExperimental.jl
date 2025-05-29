```
BiCGStab(; maxiter=KrylovDefaults.maxiter[], tol=KrylovDefaults.tol[], verbosity=KrylovDefaults.verbosity[])

Construct an instance of the Biconjugate gradient algorithm with specified parameters,
which can be passed to `linsolve` in order to iteratively solve a linear system general
linear map. The `BiCGStab` method will search for the optimal `x` in a Krylov subspace
of maximal size `maxiter`, or stop when `norm(A*x - b) < tol`. The default verbosity level 
`verbosity` amounts to printing warnings upon lack of convergence.
```

See also: [`linsolve`](@ref), [`GMRES`](@ref), [`CG`](@ref), [`BiCG`](@ref), [`LSMR`](@ref), [`MINRES`](@ref)
