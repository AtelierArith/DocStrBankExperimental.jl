```julia
SSPRK932(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!,
           thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  A third-order, nine-stage explicit strong stability preserving (SSP) method.

Consider using `SSPRK43` instead, which uses the same main method and an improved embedded method.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Gottlieb, Sigal, David I. Ketcheson, and Chi-Wang Shu.     Strong stability preserving Runge-Kutta and multistep time discretizations.     World Scientific, 2011.
