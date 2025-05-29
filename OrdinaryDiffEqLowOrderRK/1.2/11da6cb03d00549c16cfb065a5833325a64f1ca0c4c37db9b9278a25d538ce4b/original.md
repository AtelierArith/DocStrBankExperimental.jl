```julia
SIR54(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  5th order method suited for SIR-type epidemic models.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{Kovalnogov2020RungeKuttaPS,     title={Runge–Kutta pairs suited for SIR‐type epidemic models},     author={Vladislav N. Kovalnogov and Theodore E. Simos and Ch. Tsitouras},     journal={Mathematical Methods in the Applied Sciences},     year={2020},     volume={44},     pages={5210 - 5216}     }
