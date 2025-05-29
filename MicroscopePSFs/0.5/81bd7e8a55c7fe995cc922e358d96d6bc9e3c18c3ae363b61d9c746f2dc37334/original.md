```
SplinePSF(psf::AbstractPSF, 
          x_range::AbstractRange, 
          y_range::AbstractRange,
          z_range::AbstractRange;
          order::Integer=3)
```

Create a 3D SplinePSF by sampling an existing PSF on a regular grid.

# Arguments

  * `psf`: Source PSF to sample
  * `x_range`: Range of x-coordinates to sample in microns
  * `y_range`: Range of y-coordinates to sample in microns
  * `z_range`: Range of z-coordinates to sample in microns
  * `order`: Interpolation order (default: 3 for cubic)

# Returns

  * `SplinePSF`: A spline interpolation of the sampled PSF

# Example

```julia
# Create a spline from a ScalarPSF with 1µm spacing over 4µm range
scalar_psf = ScalarPSF(1.4, 0.532, 1.518)  # NA=1.4, λ=532nm, n=1.518
x_range = y_range = range(-2.0, 2.0, length=41)
z_range = range(-1.0, 1.0, length=21)
spline_psf = SplinePSF(scalar_psf, x_range, y_range, z_range)
```
