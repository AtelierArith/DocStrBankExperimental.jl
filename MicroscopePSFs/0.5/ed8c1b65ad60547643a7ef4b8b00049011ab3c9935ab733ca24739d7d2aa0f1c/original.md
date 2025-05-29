```
VectorPupilFunction{T}
```

Vector pupil function storing Ex,Ey field components as PupilFunctions.

# Fields

  * `nₐ::T`: Numerical aperture
  * `λ::T`: Wavelength in μm
  * `n_medium::T`: Refractive index of the sample medium
  * `n_coverslip::T`: Refractive index of the coverslip
  * `n_immersion::T`: Refractive index of the immersion medium
  * `Ex::PupilFunction{T}`: x-component of electric field
  * `Ey::PupilFunction{T}`: y-component of electric field
