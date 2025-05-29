```julia
QPRK98(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
         step_limiter! = OrdinaryDiffEq.trivial_limiter!,
         thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  Runge–Kutta pairs of orders 9(8) for use in quadruple precision computations

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Kovalnogov VN, Fedorov RV, Karpukhina TV, Simos TE, Tsitouras C. Runge–Kutta pairs      of orders 9 (8) for use in quadruple precision computations. Numerical Algorithms, 2023.      doi: https://doi.org/10.1007/s11075-023-01632-8
