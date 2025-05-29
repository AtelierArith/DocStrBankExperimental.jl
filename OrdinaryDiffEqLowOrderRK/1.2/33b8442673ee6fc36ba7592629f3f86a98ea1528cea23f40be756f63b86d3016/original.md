```julia
BS5(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False(),
      lazy = true)
```

Explicit Runge-Kutta Method.  Bogacki-Shampine 5/4 Runge-Kutta method. (lazy 5th order interpolant).

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `lazy`: determines if the lazy interpolant is used.

## References

@article{bogacki1996efficient,     title={An efficient runge-kutta (4, 5) pair},     author={Bogacki, P and Shampine, Lawrence F},     journal={Computers \& Mathematics with Applications},     volume={32},     number={6},     pages={15–28},     year={1996},     publisher={Elsevier}     }
