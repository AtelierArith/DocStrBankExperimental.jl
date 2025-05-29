```
amplitude(psf::ScalarPSF{T}, x::Real, y::Real, z::Real) where {T}
```

Calculate complex amplitude at a 3D position using scalar diffraction theory.

# Arguments

  * `psf`: ScalarPSF instance
  * `x, y, z`: Position in microns relative to PSF center

# Returns

  * Complex amplitude at the specified position

# Notes

  * Uses Fourier optics to propagate from pupil to image space
  * Accounts for defocus and aberrations encoded in the pupil function
