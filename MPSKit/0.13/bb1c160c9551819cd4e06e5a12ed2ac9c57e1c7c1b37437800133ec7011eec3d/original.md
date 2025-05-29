```julia
struct VUMPS{F} <: MPSKit.Algorithm
```

Variational optimization algorithm for uniform matrix product states, based on the combination of DMRG with matrix product state tangent space concepts.

## Fields

  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int64`: maximal amount of iterations
  * `verbosity::Int64`: setting for how much information is displayed
  * `alg_gauge::Any`: algorithm used for gauging the `InfiniteMPS`
  * `alg_eigsolve::Any`: algorithm used for the eigenvalue solvers
  * `alg_environments::Any`: algorithm used for the MPS environments
  * `finalize::Any`: callback function applied after each iteration, of signature `finalize(iter, ψ, H, envs) -> ψ, envs`

## References

  * [Zauner-Stauber et al. Phys. Rev. B 97 (2018)](@cite zauner-stauber2018)
  * [Vanderstraeten et al. SciPost Phys. Lect. Notes 7 (2019)](@cite vanderstraeten2019)
