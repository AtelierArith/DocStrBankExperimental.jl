```
integrate_pixels_amplitude(
    psf::AbstractPSF, 
    pixel_edges_x::AbstractVector,
    pixel_edges_y::AbstractVector,
    emitter::AbstractEmitter; 
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

Integrate PSF complex amplitude over camera pixels with optional support region optimization.

For each pixel in the specified region, numerically integrates the PSF amplitude using the specified sampling density. Unlike intensity integration, returns unnormalized complex amplitudes which can be used for coherent calculations. Automatically handles z-coordinate if both PSF and emitter support it.

# Arguments

  * `psf::AbstractPSF`: Point spread function to integrate
  * `pixel_edges_x::AbstractVector`: X-coordinate edges of pixels in microns
  * `pixel_edges_y::AbstractVector`: Y-coordinate edges of pixels in microns
  * `emitter::AbstractEmitter`: Emitter with position in microns relative to camera
  * `support`: Region to calculate (default: Inf = full image)

      * If Real: radius in microns around emitter
      * If Tuple: explicit (x*min, x*max, y*min, y*max) in microns
  * `sampling::Integer=2`: Number of samples per pixel in each dimension
  * `threaded::Bool=true`: Whether to use multi-threading for integration

# Returns

  * `Matrix{Complex{T}}`: Integrated complex amplitudes where T matches emitter.photons type
  * Array is indexed as [y,x] with [1,1] at top-left pixel
  * Values are not normalized to preserve complex amplitude relationships

# Notes

  * For coherent calculations, use this function instead of `integrate_pixels`
  * Return type is complex to support PSFs with phase information
  * To get intensity from amplitude: `abs2.(integrate_pixels_amplitude(...))`

See also: [`integrate_pixels`](@ref), [`AbstractPSF`](@ref)
