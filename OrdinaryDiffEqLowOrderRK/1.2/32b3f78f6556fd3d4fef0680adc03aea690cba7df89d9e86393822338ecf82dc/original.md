```julia
PSRK3p5q4(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
            step_limiter! = OrdinaryDiffEq.trivial_limiter!,
            thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  4-stage Pseudo-Symplectic method.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{Aubry1998,     author = {A. Aubry and P. Chartier},     journal = {BIT Numer. Math.},     title =  {Pseudo-symplectic {R}unge-{K}utta methods},     year = {1998},     },     @article{Capuano2017,     title = {Explicit {R}unge–{K}utta schemes for incompressible flow with improved energy-conservation properties},     journal = {J. Comput. Phys.},     year = {2017},     author = {F. Capuano and G. Coppola and L. Rández and L. {de Luca}},}
