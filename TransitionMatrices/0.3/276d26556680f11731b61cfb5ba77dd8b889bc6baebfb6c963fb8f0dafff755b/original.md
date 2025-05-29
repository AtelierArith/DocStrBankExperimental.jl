```
transition_matrix(s::AbstractAxisymmetricShape{T, CT}, λ, nₘₐₓ, Ng) where {T, CT}
```

Calculate the T-Matrix for a given scatterer and wavelengthg`.

Parameters:

  * `s`: the axisymmetric scatterer.
  * `λ`: the wavelength.
  * `nₘₐₓ`: the maximum order of the T-Matrix.
  * `Ng`: the number of Gauss-Legendre quadrature points to be used.

Returns:

  * `𝐓`: an `AxisymmetricTransitionMatrix` struct representing the T-Matrix.
