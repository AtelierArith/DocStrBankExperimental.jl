```julia
FRK65(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False(),
        omega = 0.0)
```

Explicit Runge-Kutta Method.  Zero Dissipation Runge-Kutta of 6th order.

### Keyword Arguments

  * `stage_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`
  * `thread`: determines whether internal broadcasting on appropriate CPU arrays should be serial (`thread = OrdinaryDiffEq.False()`) or use multiple threads (`thread = OrdinaryDiffEq.True()`) when Julia is started with multiple threads.
  * `omega`: a periodicity phase estimate,

when accurate this method results in zero numerical dissipation.

## References

@article{medvedev2018fitted, title={Fitted modifications of Runge-Kutta pairs of orders 6 (5)}, author={Medvedev, Maxim A and Simos, TE and Tsitouras, Ch}, journal={Mathematical Methods in the Applied Sciences}, volume={41}, number={16}, pages={6184–6194}, year={2018}, publisher={Wiley Online Library}}
