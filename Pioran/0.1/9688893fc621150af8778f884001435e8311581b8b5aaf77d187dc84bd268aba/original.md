```
 SHO(A, ω₀, Q)
```

Simple Harmonic Oscillator covariance Function

  * `A`: the amplitude of the covariance function
  * `ω₀`: the angular frequency of the simple harmonic oscillator
  * `Q`: the quality factor of the simple harmonic oscillator

$$
k(τ) = A \exp(-ω₀ τ / Q / 2) \left\{\begin{matrix} 2(1 + ω₀ τ) & Q = 1/2 \\ \cos(η ω₀ τ) + \frac{\sin(η ω₀ τ)}{2η Q} & Q < 1/2 \\ \cosh(η ω₀ τ) + \frac{\sinh(η ω₀ τ)}{2η Q} & Q \geq 1/2 \end{matrix}\right.\\
η = \sqrt{\left|1 - \frac{1}{4 Q^2}\right|}
$$

See [Foreman-Mackey et al. (2017)](https://ui.adsabs.harvard.edu/abs/2017AJ....154..220F) for more details.
