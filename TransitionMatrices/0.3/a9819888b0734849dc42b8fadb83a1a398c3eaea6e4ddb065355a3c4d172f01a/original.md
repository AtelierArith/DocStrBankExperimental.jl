```
expansion_coefficients(𝐓::AxisymmetricTransitionMatrix{CT, N, V, T}, λ) where {CT, N, V, T}
```

Calculate the expansion coefficients from an axisymmetric T-Matrix. Translated from Mishchenko et al.'s Fortran code.

Parameters:

  * `𝐓`: The precalculated T-Matrix of a scatterer.
  * `λ`: The wavelength.
