```julia
struct TDVP{A, F} <: MPSKit.Algorithm
```

Single site MPS time-evolution algorithm based on the Time-Dependent Variational Principle.

## Fields

  * `integrator::Any`: algorithm used in the exponential solvers
  * `tolgauge::Float64`: tolerance for gauging algorithm
  * `gaugemaxiter::Int64`: maximal amount of iterations for gauging algorithm
  * `finalize::Any`: callback function applied after each iteration, of signature `finalize(iter, ψ, H, envs) -> ψ, envs`

## References

  * [Haegeman et al. Phys. Rev. Lett. 107 (2011)](@cite haegeman2011)
