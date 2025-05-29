```
VectorPSF(nₐ::Real, λ::Real, dipole::DipoleVector;
            base_pupil::Union{Nothing, PupilFunction}=nothing,
            base_zernike::Union{Nothing, ZernikeCoefficients}=nothing,
            n_medium::Real=1.33,
            n_coverslip::Real=1.52,
            n_immersion::Real=1.52,
            z_stage::Real=0.0,
            grid_size::Integer=128)
```

Create a vector PSF using either a pupil-based or Zernike-based approach.

# Arguments

  * `nₐ`: Numerical aperture
  * `λ`: Wavelength in microns
  * `dipole`: Dipole orientation vector

# Keyword Arguments

  * `base_pupil`: Optional base aberration pupil function
  * `base_zernike`: Optional Zernike coefficients for base aberration
  * `n_medium`: Sample medium refractive index (default: 1.33)
  * `n_coverslip`: Cover slip refractive index (default: 1.52)
  * `n_immersion`: Immersion medium refractive index (default: 1.52)
  * `z_stage`: Distance the sample stage was moved away from the nominal focal plane at the coverslip (μm) (default: 0.0)
  * `grid_size`: Size of pupil grid (default: 128)

# Returns

  * VectorPSF instance
