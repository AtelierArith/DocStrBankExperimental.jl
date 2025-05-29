```julia
SHLDDRK52(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
            step_limiter! = OrdinaryDiffEq.trivial_limiter!,
            thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  Low dissipation and dispersion Runge-Kutta schemes for computational acoustics

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{stanescu19982n,     title={2N-storage low dissipation and dispersion Runge-Kutta schemes for computational acoustics},     author={Stanescu, D and Habashi, WG},     journal={Journal of Computational Physics},     volume={143},     number={2},     pages={674–681},     year={1998},     publisher={Elsevier}}
