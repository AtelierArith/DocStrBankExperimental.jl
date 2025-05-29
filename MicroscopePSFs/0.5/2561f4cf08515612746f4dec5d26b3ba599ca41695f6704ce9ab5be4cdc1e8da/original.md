```
integrate_pixels_amplitude(
    psf::AbstractPSF, 
    camera::AbstractCamera, 
    emitter::AbstractEmitter;
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

Integrate PSF complex amplitude over camera pixels with optional support region optimization.

This version takes a camera object instead of explicit pixel edges.

# Arguments

  * `psf::AbstractPSF`: Point spread function to integrate
  * `camera::AbstractCamera`: Camera geometry defining pixel edges in microns
  * `emitter::AbstractEmitter`: Emitter with position in microns relative to camera
  * `support`: Region to calculate (default: Inf = full image)

      * If Real: radius in microns around emitter
      * If Tuple: explicit (x*min, x*max, y*min, y*max) in microns
  * `sampling::Integer=2`: Number of samples per pixel in each dimension
  * `threaded::Bool=true`: Whether to use multi-threading for integration

# Returns

  * Matrix of complex amplitudes
  * Array indices start at [1,1] for top-left pixel

See also: [`integrate_pixels`](@ref), [`AbstractPSF`](@ref)
