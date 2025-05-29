```
integrate_pixels_amplitude(
    psf::SplinePSF,
    camera::AbstractCamera,
    emitter::AbstractEmitter;
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

Integrate PSF amplitude (complex) over camera pixels.

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

  * Array of integrated PSF complex amplitudes with dimensions [ny, nx]

# Notes

  * For 3D SplinePSFs (when z_range is defined), requires an emitter with a z-coordinate
