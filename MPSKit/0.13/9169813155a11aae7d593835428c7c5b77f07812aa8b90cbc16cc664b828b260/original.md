```julia
struct IDMRG{A} <: MPSKit.Algorithm
```

Single site infinite DMRG algorithm for finding the dominant eigenvector.

## Fields

  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int64`: maximal amount of iterations
  * `verbosity::Int64`: setting for how much information is displayed
  * `alg_gauge::Any`: algorithm used for gauging the MPS
  * `alg_eigsolve::Any`: algorithm used for the eigenvalue solvers
