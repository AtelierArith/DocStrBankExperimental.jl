```julia
DGLDDRK84_C(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
              step_limiter! = OrdinaryDiffEq.trivial_limiter!,
              thread = OrdinaryDiffEq.False(),
              williamson_condition = true)
```

Explicit Runge-Kutta Method.  8-stage, fourth order low-storage low-dissipation, low-dispersion scheme for discontinuous Galerkin space discretizations applied to wave propagation problems. Optimized for PDE discretizations when maximum spatial step is small due to geometric features of computational domain. Fixed timestep only.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `williamson_condition`: allows for an optimization that allows fusing broadcast expressions with the function call `f`. However, it only works for `Array` types.

## References

T. Toulorge, W. Desmet.     Optimal Runge–Kutta Schemes for Discontinuous Galerkin Space Discretizations     Applied to Wave Propagation Problems.     Journal of Computational Physics, 231(4), pp 2067-2091, 2012.     doi: https://doi.org/10.1016/j.jcp.2011.11.024
