```
iterated_integrals(W::Real, h::Real, eps::Real=0.0; ito_correction=true, kwargs...)
```

In the case of a scalar Brownian motion the integral can be explicitly calculated as $\int_0^h\int_0^sdW(t)dW(s) = \frac{1}{2}W(h)^2 - \frac{1}{2}h$.

The parameter `eps` (as well as all additional keyword arguments) has no effect but is available  to provide the same interface as the multidimensional version.
