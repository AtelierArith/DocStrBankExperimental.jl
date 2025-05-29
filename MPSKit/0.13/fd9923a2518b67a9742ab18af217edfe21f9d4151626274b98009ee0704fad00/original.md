```julia
struct DMRG{A, F} <: MPSKit.Algorithm
```

Single-site DMRG algorithm for finding the dominant eigenvector.

## Fields

  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int64`: maximal amount of iterations
  * `verbosity::Int64`: setting for how much information is displayed
  * `alg_eigsolve::Any`: algorithm used for the eigenvalue solvers
  * `finalize::Any`: callback function applied after each iteration, of signature `finalize(iter, ψ, H, envs) -> ψ, envs`
