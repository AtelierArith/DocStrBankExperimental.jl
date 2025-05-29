```
integrate_pixels_amplitude(
    psf::AbstractPSF,
    pixel_edges_x::AbstractVector,
    pixel_edges_y::AbstractVector,
    emitters::Vector{<:AbstractEmitter};
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

Integrate PSF complex amplitude over camera pixels for multiple emitters with optional support region optimization.

# Arguments

  * `psf`: Point spread function to integrate
  * `pixel_edges_x`, `pixel_edges_y`: Arrays defining pixel edge coordinates
  * `emitters`: Vector of emitters with position information
  * `support`: Region to calculate for each emitter (default: Inf = full image)
  * `sampling`: Subpixel sampling density (default: 2)
  * `threaded`: Whether to use multi-threading for integration (default: true)

# Returns

  * Array of integrated complex amplitudes
  * Values represent coherently summed field contributions

# Notes

  * Results are the coherent sum of individual emitter field contributions
  * For incoherent addition, use `abs2.(integrate_pixels_amplitude(...))` or use `integrate_pixels`
