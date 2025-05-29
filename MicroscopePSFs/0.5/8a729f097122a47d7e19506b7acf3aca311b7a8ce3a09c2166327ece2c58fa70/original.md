```
integrate_pixels(
    psf::AbstractPSF,
    camera::AbstractCamera,
    emitters::Vector{<:AbstractEmitter};
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

Integrate PSF intensity over camera pixels for multiple emitters with optional support region optimization. This version takes a camera object instead of explicit pixel edges.

# Arguments

  * `psf`: Point spread function to integrate
  * `camera`: Camera geometry defining pixel edges
  * `emitters`: Vector of emitters with position information
  * `support`: Region to calculate for each emitter (default: Inf = full image)
  * `sampling`: Subpixel sampling density (default: 2)
  * `threaded`: Whether to use multi-threading for integration (default: true)

# Returns

  * Array of integrated PSF intensities with dimensions matching the camera
  * Values represent actual photon counts from all emitters
