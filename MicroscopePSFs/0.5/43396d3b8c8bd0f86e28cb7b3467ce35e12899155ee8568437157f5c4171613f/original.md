```
VectorPSF(nₐ::Real, λ::Real;
            base_pupil::Union{Nothing, PupilFunction}=nothing,
            base_zernike::Union{Nothing, ZernikeCoefficients}=nothing,
            n_medium::Real=1.33,
            n_coverslip::Real=1.52,
            n_immersion::Real=1.52,
            z_stage::Real=0.0,
            grid_size::Integer=128)
```

Create a vector PSF with a rotating dipole, modeled as an incoherent sum of  x, y, and z dipole orientations.

# Arguments

  * `nₐ`: Numerical aperture
  * `λ`: Wavelength in microns

# Keyword Arguments

  * `base_pupil`: Optional base aberration pupil function
  * `base_zernike`: Optional Zernike coefficients for base aberration
  * `n_medium`: Sample medium refractive index (default: 1.33)
  * `n_coverslip`: Cover slip refractive index (default: 1.52)
  * `n_immersion`: Immersion medium refractive index (default: 1.52)
  * `z_stage`: Distance the sample stage was moved away from the nominal focal plane at the coverslip (μm) (default: 0.0)
  * `grid_size`: Size of pupil grid (default: 128)

# Returns

  * VectorPSF instance representing a rotating dipole

# Notes

  * Intensity is calculated as incoherent average of three orthogonal dipole orientations
  * The amplitude() function is not meaningful for rotating dipoles and will throw an error
