```
CarrMadan <: AbstractPricingMethod
```

Fourier transform-based pricing method for European options.

Implements the Carr-Madan method, which prices European options using the inverse Fourier transform of the characteristic function of the log-price under the risk-neutral measure.

# Fields

  * `α`: Damping factor to ensure integrability of the Fourier transform.
  * `bound`: Integration bound for numerical quadrature.
  * `dynamics`: The model dynamics providing the terminal characteristic function.
  * `kwargs`: Additional keyword arguments passed to the integral solver.
