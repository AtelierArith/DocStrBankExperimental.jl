```
(psf::SplinePSF)(x::Real, y::Real, z::Real)
```

Evaluate the 3D spline PSF at position (x, y, z).

# Arguments

  * `x, y, z`: Coordinates in microns relative to PSF center

# Returns

  * PSF intensity at the specified position

# Notes

  * Returns 0 if the position is outside the PSF boundary
  * Preserves the normalization of the original PSF data

# Example

```julia
# Evaluate a 3D SplinePSF at a specific point
intensity = spline_psf(0.1, 0.2, 0.3)
```
