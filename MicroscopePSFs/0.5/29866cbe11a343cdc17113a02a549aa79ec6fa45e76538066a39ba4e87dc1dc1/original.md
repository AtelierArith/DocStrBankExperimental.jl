```
VectorPupilFunction(nₐ::Real, λ::Real, n_medium::Real, n_coverslip::Real, n_immersion::Real, grid_size::Integer)
```

Create a vector pupil function with empty field components.

# Arguments

  * `nₐ`: Numerical aperture
  * `λ`: Wavelength in μm
  * `n_medium`: Sample medium refractive index
  * `n_coverslip`: Cover slip refractive index
  * `n_immersion`: Immersion medium refractive index
  * `grid_size`: Size of pupil grid (grid*size × grid*size)

# Returns

  * `VectorPupilFunction` with zero-initialized field components
