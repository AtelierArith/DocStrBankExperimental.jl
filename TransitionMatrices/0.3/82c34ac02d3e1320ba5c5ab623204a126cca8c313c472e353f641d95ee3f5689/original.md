```
expansion_coefficients(𝐓::AbstractTransitionMatrix{CT, N}, λ) where {CT, N}
```

Calculate the expansion coefficients from an arbitrary T-Matrix, using Eq. (24) – (74) in Bi et al. (2014).

Parameters:

  * `𝐓`: The precalculated T-Matrix of a scatterer.
  * `λ`: The wavelength.

Keyword arguments:

  * `full`: Whether to return the full expansion coefficients (`β₃` to `β₆`). Default to `false`.
