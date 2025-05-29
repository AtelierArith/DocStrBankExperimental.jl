```julia
TSLDDRK74(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
            step_limiter! = OrdinaryDiffEq.trivial_limiter!,
            thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  Low-Storage Method 7-stage, fourth order low-storage low-dissipation, low-dispersion scheme with maximal accuracy and stability limit along the imaginary axes. Fixed timestep only.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Kostas Tselios, T. E. Simos. Optimized Runge–Kutta Methods with Minimal Dispersion and Dissipation     for Problems arising from Computational Acoustics. Physics Letters A, 393(1-2), pp 38-47, 2007.     doi: https://doi.org/10.1016/j.physleta.2006.10.072
