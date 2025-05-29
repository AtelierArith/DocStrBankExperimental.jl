```
integrate_pixels(
    psf::SplinePSF,
    camera::AbstractCamera,
    emitter::AbstractEmitter;
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

Integrate PSF over camera pixels using interpolation.

# Arguments

  * `psf`: SplinePSF instance
  * `camera`: Camera geometry
  * `emitter`: Emitter with position information
  * `support`: Region to calculate (default: Inf = full image)

      * If Real: radius in microns around emitter
      * If Tuple: explicit (x*min, x*max, y*min, y*max) in microns
  * `sampling`: Subpixel sampling density for integration accuracy
  * `threaded`: Whether to use multi-threading for integration (default: true)

# Returns

  * Array of integrated PSF intensities with dimensions [ny, nx]
  * Values represent actual photon counts based on emitter's photon value

# Notes

  * For 3D SplinePSFs (when z_range is defined), requires an emitter with a z-coordinate
