```julia
SSPRK104(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!,
           thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  A fourth-order, ten-stage explicit strong stability preserving (SSP) method. Fixed timestep only.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Ketcheson, David I.     Highly efficient strong stability-preserving Runge–Kutta methods with     low-storage implementations.     SIAM Journal on Scientific Computing 30.4 (2008): 2113-2136.
