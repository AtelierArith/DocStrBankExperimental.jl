```julia
DP5(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  Dormand-Prince's 5/4 Runge-Kutta method. (free 4th order interpolant).

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{dormand1980family,     title={A family of embedded Runge-Kutta formulae},     author={Dormand, John R and Prince, Peter J},     journal={Journal of computational and applied mathematics},     volume={6},     number={1},     pages={19–26},     year={1980},     publisher={Elsevier}     }
