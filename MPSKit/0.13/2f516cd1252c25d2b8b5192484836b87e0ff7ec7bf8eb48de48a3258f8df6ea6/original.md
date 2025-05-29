```julia
struct DMRG2{A, S, F} <: MPSKit.Algorithm
```

Two-site DMRG algorithm for finding the dominant eigenvector.

## Fields

  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int64`: maximal amount of iterations
  * `verbosity::Int64`: setting for how much information is displayed
  * `alg_eigsolve::Any`: algorithm used for the eigenvalue solvers
  * `alg_svd::Any`: algorithm used for the singular value decomposition
  * `trscheme::TensorKit.TruncationScheme`: algorithm used for [truncation](@extref TensorKit.tsvd) of the two-site update
  * `finalize::Any`: callback function applied after each iteration, of signature `finalize(iter, ψ, H, envs) -> ψ, envs`
