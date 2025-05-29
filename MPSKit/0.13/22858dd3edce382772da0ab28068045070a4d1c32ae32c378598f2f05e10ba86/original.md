```julia
struct IDMRG2{A, S} <: MPSKit.Algorithm
```

Two-site infinite DMRG algorithm for finding the dominant eigenvector.

## Fields

  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int64`: maximal amount of iterations
  * `verbosity::Int64`: setting for how much information is displayed
  * `alg_gauge::Any`: algorithm used for gauging the MPS
  * `alg_eigsolve::Any`: algorithm used for the eigenvalue solvers
  * `alg_svd::Any`: algorithm used for the singular value decomposition
  * `trscheme::TensorKit.TruncationScheme`: algorithm used for [truncation](@extref TensorKit.tsvd) of the two-site update
