```
SplinePSF(psf::AbstractPSF, 
          x_range::AbstractRange, 
          y_range::AbstractRange;
          order::Integer=3)
```

Create a 2D SplinePSF by sampling a PSF on a 2D grid (at z=0).

# Arguments

  * `psf`: Source PSF to sample
  * `x_range`: Range of x-coordinates to sample in microns
  * `y_range`: Range of y-coordinates to sample in microns
  * `order`: Interpolation order (default: 3 for cubic)

# Returns

  * `SplinePSF`: A 2D spline interpolation of the sampled PSF

# Note

  * For 3D PSFs, this samples at z=0 only
