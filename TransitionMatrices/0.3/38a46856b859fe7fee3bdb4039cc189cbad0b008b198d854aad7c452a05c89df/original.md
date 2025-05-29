```
transition_matrix_iitm(s::AbstractAxisymmetricShape{T, CT}, λ, nₘₐₓ, Nr, Nϑ; rₘᵢₙ) where {T, CT}
```

Use IITM to calculate the T-Matrix for a given scatterer and wavelength.

Parameters:

  * `s`: the axisymmetric scatterer.
  * `λ`: the wavelength.
  * `nₘₐₓ`: the maximum order of the T-Matrix.
  * `Nr`: the number of radial quadrature points to be used.
  * `Nϑ`: the number of zenithal quadrature points to be used.

Keyword arguments:

  * `rₘᵢₙ`: the starting point of the radial quadrature. Default to `rmin(s)`, which is the radius of the maximum inscribed sphere.

Returns:

  * `𝐓`: an `AxisymmetricTransitionMatrix` struct representing the T-Matrix.
