```julia
ORK256(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
         step_limiter! = OrdinaryDiffEq.trivial_limiter!,
         thread = OrdinaryDiffEq.False(),
         williamson_condition = true)
```

Explicit Runge-Kutta Method.  A second-order, five-stage method for wave propagation equations. Fixed timestep only.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `williamson_condition`: allows for an optimization that allows fusing broadcast expressions with the function call `f`. However, it only works for `Array` types.

## References

Matteo Bernardini, Sergio Pirozzoli.     A General Strategy for the Optimization of Runge-Kutta Schemes for Wave     Propagation Phenomena.     Journal of Computational Physics, 228(11), pp 4182-4199, 2009.     doi: https://doi.org/10.1016/j.jcp.2009.02.032
