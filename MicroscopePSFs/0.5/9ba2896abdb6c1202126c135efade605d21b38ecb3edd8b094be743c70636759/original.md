```
amplitude(psf::SplinePSF, x::Real, y::Real)
```

Calculate the complex amplitude of the PSF at position (x, y) with z=0.

# Arguments

  * `psf`: SplinePSF instance
  * `x, y`: Coordinates in microns relative to PSF center

# Returns

  * Complex amplitude = sqrt(intensity) with zero phase
