```julia
RK4(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  The canonical Runge-Kutta Order 4 method. Uses a defect control for adaptive stepping using maximum error over the whole interval.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{shampine2005solving,       title={Solving ODEs and DDEs with residual control},       author={Shampine, LF},       journal={Applied Numerical Mathematics},       volume={52},       number={1},       pages={113–127},       year={2005},       publisher={Elsevier}       }
