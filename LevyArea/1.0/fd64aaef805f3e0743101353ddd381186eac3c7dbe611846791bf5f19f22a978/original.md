```
iterated_integrals(W::Real, q_12::Real, h::Real, eps::Real; ito_correction=true, kwargs...)
```

In the case of a scalar Q-Wiener process with (scalar) covariance Q the integral can be explicitly calculated as $\int_0^h\int_0^sdW(t)dW(s) = \frac{1}{2}W(h)^2 - \frac{1}{2}hQ$.

Note that, as in the multidimensional case, the parameter `q_12` denotes the square root of the covariance.

The parameter `eps` (as well as all additional keyword arguments) has no effect but is available  to provide the same interface as the multidimensional version.
