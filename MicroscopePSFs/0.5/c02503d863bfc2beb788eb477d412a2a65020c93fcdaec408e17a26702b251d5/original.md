```
AiryPSF{T<:AbstractFloat} <: Abstract2DPSF{T}
```

2D Airy pattern PSF using paraxial, scalar model.

Field amplitude for a circular aperture is given by:     A(r) = ν/√(4π) * (2J₁(νr)/(νr)) where:     ν = 2π*nₐ/λ     J₁ is the Bessel function of first kind, order 1     r is the radial distance from optical axis

# Fields

  * `nₐ`: Numerical aperture
  * `λ`: Wavelength in microns
  * `ν`: Optical parameter = 2π*nₐ/λ
