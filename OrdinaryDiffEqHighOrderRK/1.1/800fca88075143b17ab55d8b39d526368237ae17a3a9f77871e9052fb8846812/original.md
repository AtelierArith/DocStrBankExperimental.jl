```julia
TsitPap8(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!,
           thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  Tsitouras-Papakostas 8/7 Runge-Kutta method.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References
