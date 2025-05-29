```julia
KYK2014DGSSPRK_3S2(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                     step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                     thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  Optimal strong-stability-preserving Runge-Kutta time discretizations for discontinuous Galerkin methods

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{kubatko2014optimal, title={Optimal strong-stability-preserving Runge–Kutta time discretizations for discontinuous Galerkin methods}, author={Kubatko, Ethan J and Yeager, Benjamin A and Ketcheson, David I}, journal={Journal of Scientific Computing}, volume={60}, pages={313–344}, year={2014}, publisher={Springer}}
