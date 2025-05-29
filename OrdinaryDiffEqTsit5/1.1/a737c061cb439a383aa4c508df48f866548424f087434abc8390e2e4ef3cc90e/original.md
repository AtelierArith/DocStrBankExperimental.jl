```julia
Tsit5(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  A fifth-order explicit Runge-Kutta method with embedded error estimator of Tsitouras. Free 4th order interpolant.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{tsitouras2011runge,     title={Runge–Kutta pairs of order 5 (4) satisfying only the first column simplifying assumption},     author={Tsitouras, Ch},     journal={Computers \& Mathematics with Applications},     volume={62},     number={2},     pages={770–775},     year={2011},     publisher={Elsevier}     }
