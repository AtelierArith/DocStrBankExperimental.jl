```julia
ParsaniKetchesonDeconinck3S205(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                                 step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                                 thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  Low-Storage Method 20-stage, fifth order (3S) low-storage scheme, optimized for the spectral difference method applied to wave propagation problems.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Parsani, Matteo, David I. Ketcheson, and W. Deconinck.     Optimized explicit Runge–Kutta schemes for the spectral difference method applied to wave propagation problems.     SIAM Journal on Scientific Computing 35.2 (2013): A957-A986.     doi: https://doi.org/10.1137/120885899
