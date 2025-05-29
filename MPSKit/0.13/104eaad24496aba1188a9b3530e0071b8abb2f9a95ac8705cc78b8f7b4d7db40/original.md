```julia
struct TDVP2{A, S, F} <: MPSKit.Algorithm
```

Two-site MPS time-evolution algorithm based on the Time-Dependent Variational Principle.

## Fields

  * `integrator::Any`: algorithm used in the exponential solvers
  * `tolgauge::Float64`: tolerance for gauging algorithm
  * `gaugemaxiter::Int64`: maximal amount of iterations for gauging algorithm
  * `alg_svd::Any`: algorithm used for the singular value decomposition
  * `trscheme::TensorKit.TruncationScheme`: algorithm used for truncation of the two-site update
  * `finalize::Any`: callback function applied after each iteration, of signature `finalize(iter, ψ, H, envs) -> ψ, envs`

## References

  * [Haegeman et al. Phys. Rev. Lett. 107 (2011)](@cite haegeman2011)
