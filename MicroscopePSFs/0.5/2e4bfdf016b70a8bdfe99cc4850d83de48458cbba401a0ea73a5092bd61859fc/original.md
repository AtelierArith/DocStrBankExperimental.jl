```
SplinePSF(psf_stack::AbstractArray{<:Real,3}, 
          x_range::AbstractRange,
          y_range::AbstractRange,
          z_range::AbstractRange;
          order::Integer=3)
```

Construct a 3D SplinePSF from a PSF stack and coordinate ranges.

# Arguments

  * `psf_stack`: 3D array containing the PSF data with dimensions [y, x, z]
  * `x_range`: Range of uniformly spaced x coordinates in microns
  * `y_range`: Range of uniformly spaced y coordinates in microns
  * `z_range`: Range of uniformly spaced z coordinates in microns
  * `order`: Interpolation order (default: 3 for cubic B-splines)

# Returns

  * `SplinePSF`: A 3D spline interpolation of the PSF

# Examples

```julia
# Create a 3D spline from sampled intensity values
x_range = y_range = range(-2.0, 2.0, length=41)  # 41×41 lateral samples with 0.1μm spacing
z_range = range(-1.0, 1.0, length=21)            # 21 axial samples with 0.1μm spacing
psf_values = zeros(Float64, 41, 41, 21)          # Fill with your PSF values
spline_psf = SplinePSF(psf_values, x_range, y_range, z_range)
```
