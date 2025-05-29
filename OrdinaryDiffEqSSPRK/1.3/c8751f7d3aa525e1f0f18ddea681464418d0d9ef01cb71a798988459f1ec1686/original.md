```julia
SSPRK43(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
          step_limiter! = OrdinaryDiffEq.trivial_limiter!,
          thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  A third-order, four-stage explicit strong stability preserving (SSP) method.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

Optimal third-order explicit SSP method with four stages discovered by

  * J. F. B. M. Kraaijevanger. "Contractivity of Runge-Kutta methods." In: BIT Numerical Mathematics 31.3 (1991), pp. 482–528. [DOI: 10.1007/BF01933264](https://doi.org/10.1007/BF01933264).

Embedded method constructed by

  * Sidafa Conde, Imre Fekete, John N. Shadid. "Embedded error estimation and adaptive step-size control for optimal explicit strong stability preserving Runge–Kutta methods." [arXiv: 1806.08693](https://arXiv.org/abs/1806.08693)

Efficient implementation (and optimized controller) developed by

  * Hendrik Ranocha, Lisandro Dalcin, Matteo Parsani, David I. Ketcheson (2021) Optimized Runge-Kutta Methods with Automatic Step Size Control for Compressible Computational Fluid Dynamics [arXiv:2104.06836](https://arxiv.org/abs/2104.06836)
