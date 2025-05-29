```julia
Vern7(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False(),
        lazy = true)
```

Explicit Runge-Kutta Method.  Verner's “Most Efficient” 7/6 Runge-Kutta method. (lazy 7th order interpolant).

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `lazy`: determines if the lazy interpolant is used.

## References

@article{verner2010numerically,     title={Numerically optimal Runge–Kutta pairs with interpolants},     author={Verner, James H},     journal={Numerical Algorithms},     volume={53},     number={2-3},     pages={383–396},     year={2010},     publisher={Springer}     }
