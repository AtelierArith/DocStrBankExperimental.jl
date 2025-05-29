```julia
RKM(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  Method designed to have good stability properties when applied to pseudospectral discretizations of hyperbolic partial differential equaitons.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{mead1999optimal,   title={Optimal Runge–Kutta methods for first order pseudospectral operators},   author={Mead, JL and Renaut, RA},   journal={Journal of Computational Physics},   volume={152},   number={1},   pages={404–419},   year={1999},   publisher={Elsevier} }
