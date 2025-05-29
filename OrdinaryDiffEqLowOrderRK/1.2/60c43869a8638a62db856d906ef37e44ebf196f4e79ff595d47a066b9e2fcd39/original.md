```julia
Anas5(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False(),
        w = 1)
```

Explicit Runge-Kutta Method.  4th order Runge-Kutta method designed for periodic problems.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `w`: a periodicity estimate, which when accurate the method becomes 5th order

(and is otherwise 4th order with less error for better estimates).

## References

@article{anastassi2005optimized, title={An optimized Runge–Kutta method for the solution of orbital problems}, author={Anastassi, ZA and Simos, TE}, journal={Journal of Computational and Applied Mathematics}, volume={175}, number={1}, pages={1–9}, year={2005}, publisher={Elsevier}}
