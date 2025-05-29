```julia
PFRK87(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
         step_limiter! = OrdinaryDiffEq.trivial_limiter!,
         thread = OrdinaryDiffEq.False(),
         omega = 0.0)
```

Explicit Runge-Kutta Method.  Phase-fitted Runge-Kutta of 8th order.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `omega`: a periodicity phase estimate,              when accurate this method results in zero numerical dissipation.

## References
