```
n_thermal(ω::Real, ω_th::Real)
```

Return the number of photons in thermal equilibrium for an harmonic oscillator mode with frequency $\omega$, at the temperature described by $\omega_{\textrm{th}} \equiv k_B T / \hbar$:

$$
n(\omega, \omega_{\textrm{th}}) = \frac{1}{e^{\omega/\omega_{\textrm{th}}} - 1},
$$

where $\hbar$ is the reduced Planck constant, and $k_B$ is the Boltzmann constant.
