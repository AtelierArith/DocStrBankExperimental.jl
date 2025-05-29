```
SplinePSF(psf::AbstractPSF; 
          lateral_range::Float64=2.0,
          axial_range::Float64=1.0,
          lateral_step::Float64=0.05,
          axial_step::Float64=0.1,
          order::Integer=3)
```

Create a SplinePSF with automatically calculated sampling ranges.

# Arguments

  * `psf`: Source PSF to sample
  * `lateral_range`: Half-width of lateral (xy) sampling range in microns
  * `axial_range`: Half-width of axial (z) sampling range in microns
  * `lateral_step`: Step size in microns for lateral (xy) sampling (default: 0.05µm = 50nm)
  * `axial_step`: Step size in microns for axial (z) sampling (default: 0.1µm = 100nm)
  * `order`: Interpolation order (default: 3 for cubic)

# Returns

  * `SplinePSF`: Either a 2D or 3D spline PSF depending on input PSF type

# Example

```julia
# Create a spline PSF with default sampling parameters
scalar_psf = ScalarPSF(1.4, 0.532, 1.518)
spline_psf = SplinePSF(scalar_psf)  # Uses default ranges and step sizes
```
