```
amplitude(psf::SplinePSF, x::Real, y::Real, z::Real)
```

Calculate the complex amplitude of the 3D PSF at position (x, y, z).

# Arguments

  * `psf`: SplinePSF instance
  * `x, y, z`: Coordinates in microns relative to PSF center

# Returns

  * Complex amplitude = sqrt(intensity) with zero phase

# Notes

  * Returns sqrt(intensity) as Complex to match the interface of other PSFs
  * The SplinePSF does not model phase information
