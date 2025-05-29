```
(psf::SplinePSF)(x::Real, y::Real)
```

Evaluate the spline PSF at position (x, y).

# Arguments

  * `x, y`: Coordinates in microns relative to PSF center

# Returns

  * PSF intensity at the specified position

# Notes

  * For 3D PSFs, evaluates at z = 0 if in range, otherwise returns 0
  * Returns 0 if the position is outside the PSF boundary
  * Preserves the normalization of the original PSF data

# Example

```julia
# Evaluate a SplinePSF at a specific point
intensity = spline_psf(0.1, 0.2)
```
