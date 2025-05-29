```
SplinePSF(psf_stack::AbstractArray{<:Real,2}, 
          x_range::AbstractRange,
          y_range::AbstractRange;
          order::Integer=3)
```

Construct a 2D SplinePSF from a PSF stack and coordinate ranges.

# Arguments

  * `psf_stack`: 2D array containing the PSF data with dimensions [y, x]
  * `x_range`: Range of uniformly spaced x coordinates in microns
  * `y_range`: Range of uniformly spaced y coordinates in microns
  * `order`: Interpolation order (default: 3 for cubic B-splines)

# Returns

  * `SplinePSF`: A 2D spline interpolation of the PSF

# Examples

```julia
# Create a 2D spline from an Airy PSF sampled on a grid
x_range = y_range = range(-2.0, 2.0, length=101)  # 101×101 grid with 40nm spacing
airy = AiryPSF(1.4, 0.532)  # NA=1.4, λ=532nm
psf_values = [airy(x, y) for y in y_range, x in x_range]
spline_psf = SplinePSF(psf_values, x_range, y_range)
```
