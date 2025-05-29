```
VectorPSF{T<:AbstractFloat} <: Abstract3DPSF{T}
```

Vector PSF model using explicit pupil function representation. Allows direct manipulation of pupil function for custom aberrations.

# Fields

  * `nₐ::T`: Numerical aperture
  * `λ::T`: Wavelength in microns
  * `n_medium::T`: Sample medium refractive index
  * `n_coverslip::T`: Cover slip refractive index
  * `n_immersion::T`: Immersion medium refractive index
  * `dipole::DipoleVector{T}`: Dipole orientation
  * `z_stage::T`: Distance the sample stage was moved away from the nominal focal plane at the coverslip (μm)
  * `vector_pupils::Vector{VectorPupilFunction{T}}`: Vector of pupil functions containing field components. For a single dipole, this contains one pupil. For a rotating dipole, it contains three pupils for x, y, and z orientations.
  * `base_pupil::Union{Nothing, PupilFunction{T}}`: Base pupil function representing system aberrations
  * `zernike_coeffs::Union{Nothing, ZernikeCoefficients{T}}`: Zernike coefficients used to create this PSF (if applicable)
