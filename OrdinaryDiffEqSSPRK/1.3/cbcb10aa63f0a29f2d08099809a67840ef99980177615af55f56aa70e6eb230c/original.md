```julia
SSPRK33(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
          step_limiter! = OrdinaryDiffEq.trivial_limiter!,
          thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  A third-order, three-stage explicit strong stability preserving (SSP) method. Fixed timestep only.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Shu, Chi-Wang, and Stanley Osher.     Efficient implementation of essentially non-oscillatory shock-capturing schemes.     Journal of Computational Physics 77.2 (1988): 439-471.     https://doi.org/10.1016/0021-9991(88)90177-5
