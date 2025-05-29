```julia
Alshina6(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!,
           thread = OrdinaryDiffEq.False())
```

Explicit Runge-Kutta Method.  6th order, 7-stage Method with optimal parameters.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.

## References

@article{Alshina2008,     doi = {10.1134/s0965542508030068},     url = {https://doi.org/10.1134/s0965542508030068},     year = {2008},     month = mar,     publisher = {Pleiades Publishing Ltd},     volume = {48},     number = {3},     pages = {395–405},     author = {E. A. Alshina and E. M. Zaks and N. N. Kalitkin},     title = {Optimal first- to sixth-order accurate Runge-Kutta schemes},     journal = {Computational Mathematics and Mathematical Physics}     }
