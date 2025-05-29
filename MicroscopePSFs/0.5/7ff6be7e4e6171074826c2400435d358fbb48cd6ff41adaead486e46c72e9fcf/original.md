```
integrate_pixels(
    psf::AbstractPSF,
    pixel_edges_x::AbstractVector,
    pixel_edges_y::AbstractVector,
    emitters::Vector{<:AbstractEmitter};
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

Integrate PSF intensity over camera pixels for multiple emitters with optional support region optimization.

# Arguments

  * `psf`: Point spread function to integrate
  * `pixel_edges_x`, `pixel_edges_y`: Arrays defining pixel edge coordinates
  * `emitters`: Vector of emitters with position information
  * `support`: Region to calculate for each emitter (default: Inf = full image)

      * If Real: radius in microns around each emitter
      * If Tuple: explicit (x*min, x*max, y*min, y*max) in microns (fixed region for all emitters)
  * `sampling`: Subpixel sampling density (default: 2)
  * `threaded`: Whether to use multi-threading for integration (default: true) Set to false when using with automatic differentiation frameworks

# Returns

  * Array of integrated PSF intensities with dimensions matching the camera
  * Values represent actual photon counts from all emitters

# Notes

  * Results are the sum of individual emitter contributions (incoherent addition)
  * For coherent addition, use `integrate_pixels_amplitude` and sum complex amplitudes
