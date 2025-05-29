```julia
BS3(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  A third-order, four-stage FSAL method with embedded error estimator of Bogacki and Shampine.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{bogacki19893,     title={A 3 (2) pair of Runge-Kutta formulas},     author={Bogacki, Przemyslaw and Shampine, Lawrence F},     journal={Applied Mathematics Letters},     volume={2},     number={4},     pages={321–325},     year={1989},     publisher={Elsevier}     }
