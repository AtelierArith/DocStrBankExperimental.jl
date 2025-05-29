```julia
struct VOMPS{F} <: MPSKit.Algorithm
```

Power method algorithm for finding dominant eigenvectors of infinite MPOs. This method works by iteratively approximating the product of an operator and a state with a new state of the same bond dimension.

## Fields

  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int64`: maximal amount of iterations
  * `verbosity::Int64`: setting for how much information is displayed
  * `alg_gauge::Any`: algorithm used for gauging the `InfiniteMPS`
  * `alg_environments::Any`: algorithm used for the MPS environments
  * `finalize::Any`: callback function applied after each iteration, of signature `finalize(iter, ψ, H, envs) -> ψ, envs`

## References

  * [Vanhecke et al. SciPost Phys. Core 4 (2021)](@cite vanhecke2021)
