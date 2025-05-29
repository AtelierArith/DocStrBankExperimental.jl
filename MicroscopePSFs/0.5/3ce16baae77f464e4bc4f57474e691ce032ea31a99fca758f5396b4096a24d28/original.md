```
ScalarPSF{T} <: Abstract3DPSF{T}
```

Scalar 3D PSF using explicit pupil function representation.

# Fields

  * `nₐ::T`: Numerical aperture
  * `λ::T`: Wavelength in microns
  * `n::T`: Refractive index
  * `pupil::PupilFunction{T}`: Complex pupil function
  * `zernike_coeffs::Union{Nothing, ZernikeCoefficients{T}}`: Zernike coefficients used to create this PSF (if applicable)

# Notes

Can be initialized with either a PupilFunction or ZernikeCoefficients using the ScalarPSF factory function.
