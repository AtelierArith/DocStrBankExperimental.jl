```
(psf::ScalarPSF)(x::Real, y::Real, z::Real)
```

Evaluate PSF intensity at the given 3D position.

# Arguments

  * `x, y, z`: Position in microns relative to PSF center

# Returns

  * Intensity value at the specified position

# Notes

  * Calculated as |amplitude|² of the complex field
  * Follows standard operator syntax: `intensity = psf(x, y, z)`
