```julia
RDPK3SpFSAL35(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  A third-order, five-stage method with embedded error estimator using the FSAL property designed for spectral element discretizations of compressible fluid mechanics.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Ranocha, Dalcin, Parsani, Ketcheson (2021)     Optimized Runge-Kutta Methods with Automatic Step Size Control for     Compressible Computational Fluid Dynamics     [arXiv:2104.06836](https://arxiv.org/abs/2104.06836)
