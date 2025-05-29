```julia
RKO65(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  5th order method.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Tsitouras, Ch. "Explicit Runge–Kutta methods for starting integration of     Lane–Emden problem." Applied Mathematics and Computation 354 (2019): 353-364.     doi: https://doi.org/10.1016/j.amc.2019.02.047
