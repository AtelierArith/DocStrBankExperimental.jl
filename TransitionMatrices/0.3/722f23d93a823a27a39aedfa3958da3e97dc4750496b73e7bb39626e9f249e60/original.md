```
amplitude_matrix(axi::AxisymmetricTransitionMatrix{CT, N, V, T}, ϑᵢ, φᵢ, ϑₛ, φₛ;
                          λ = 2π,
                          rot::Union{Nothing, Rotation{3}} = nothing) where {CT, N, V, T}
```

Calculate the amplitude matrix of an axisymmetric scatterer.

Parameters:

  * `axi`: the T-Matrix of the scatterer.
  * `ϑᵢ`: the zenith angle of the incident wave.
  * `φᵢ`: the azimuth angle of the incident wave.
  * `ϑₛ`: the zenith angle of the scattered wave.
  * `φₛ`: the azimuth angle of the scattered wave.
  * `λ`: the wavelength of the incident wave in the host medium. Default to 2π.
  * `rot`: the rotation of the scatterer.
