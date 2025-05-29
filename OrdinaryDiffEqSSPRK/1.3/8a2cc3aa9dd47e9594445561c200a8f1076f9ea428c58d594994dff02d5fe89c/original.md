```julia
SSPRKMSVS32(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
              step_limiter! = OrdinaryDiffEq.trivial_limiter!,
              thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  A second-order, three-step explicit strong stability preserving (SSP) linear multistep method. This method does not come with an error estimator and requires a fixed time step size.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Shu, Chi-Wang.     Total-variation-diminishing time discretizations.     SIAM Journal on Scientific and Statistical Computing 9, no. 6 (1988): 1073-1084.     [DOI: 10.1137/0909073](https://doi.org/10.1137/0909073)
