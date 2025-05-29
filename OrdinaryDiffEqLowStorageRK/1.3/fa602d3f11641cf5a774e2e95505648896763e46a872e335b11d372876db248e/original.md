```julia
SHLDDRK64(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
            step_limiter! = OrdinaryDiffEq.trivial_limiter!,
            thread = OrdinaryDiffEq.False(),
            williamson_condition = true)
```

Explicit Runge-Kutta Method.  A fourth-order, six-stage low-storage method. Fixed timestep only.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `williamson_condition`: allows for an optimization that allows fusing broadcast expressions with the function call `f`. However, it only works for `Array` types.

## References

D. Stanescu, W. G. Habashi.     2N-Storage Low Dissipation and Dispersion Runge-Kutta Schemes for Computational     Acoustics.     Journal of Computational Physics, 143(2), pp 674-681, 1998.     doi: https://doi.org/10.1006/jcph.1998.5986     }
