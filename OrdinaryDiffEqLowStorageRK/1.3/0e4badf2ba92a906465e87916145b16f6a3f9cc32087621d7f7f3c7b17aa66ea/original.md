```julia
CarpenterKennedy2N54(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                       step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                       thread = OrdinaryDiffEq.False(),
                       williamson_condition = true)
```

Explicit Runge-Kutta Method.  A fourth-order, five-stage low-storage method of Carpenter and Kennedy (free 3rd order Hermite interpolant). Fixed timestep only. Designed for hyperbolic PDEs (stability properties).

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `williamson_condition`: allows for an optimization that allows fusing broadcast expressions with the function call `f`. However, it only works for `Array` types.

## References

@article{carpenter1994fourth,     title={Fourth-order 2N-storage Runge-Kutta schemes},     author={Carpenter, Mark H and Kennedy, Christopher A},     year={1994}     }
