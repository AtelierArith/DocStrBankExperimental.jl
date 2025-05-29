```
SplinePSF{T<:AbstractFloat, IT<:AbstractInterpolation} <: AbstractPSF
```

A point spread function (PSF) represented as a B-spline interpolation.

# Fields

  * `spline`: The B-spline interpolation object
  * `x_range`: Range of x-coordinates used for uniform grid interpolation
  * `y_range`: Range of y-coordinates used for uniform grid interpolation
  * `z_range`: Range of z-coordinates for 3D PSFs, or `nothing` for 2D PSFs
  * `original_grid`: Original grid data used to create the interpolation
  * `interp_order`: Interpolation order used (0=constant, 1=linear, 3=cubic)

# Notes

  * Coordinates and ranges are in physical units (typically microns)
  * PSF values are preserved from the original PSF that was sampled
  * Full implementation is in spline_psf.jl
