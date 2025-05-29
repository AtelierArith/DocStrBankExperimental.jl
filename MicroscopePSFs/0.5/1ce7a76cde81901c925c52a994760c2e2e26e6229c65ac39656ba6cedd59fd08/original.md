```
PupilFunction(nₐ::Real, λ::Real, n::Real, 
              zc::ZernikeCoefficients;
              grid_size::Int=64)
```

Create a PupilFunction from ZernikeCoefficients type.

# Arguments

  * `nₐ`: Numerical aperture
  * `λ`: Wavelength in microns
  * `n`: Refractive index
  * `zc`: ZernikeCoefficients containing amplitude and phase coefficients

# Keyword Arguments

  * `grid_size`: Size of square sampling grid (default: 64)

# Returns

  * `PupilFunction` with complex field computed from Zernike polynomials
