```julia
TanYam7(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
          step_limiter! = OrdinaryDiffEq.trivial_limiter!,
          thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  Tanaka-Yamashita 7 Runge-Kutta method. (7th order interpolant).

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Tanaka M., Muramatsu S., Yamashita S., (1992), On the Optimization of Some Nine-Stage     Seventh-order Runge-Kutta Method, Information Processing Society of Japan,     33 (12), pp. 1512-1526.
