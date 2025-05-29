```
integrate_pixels(
    psf::AbstractPSF, 
    pixel_edges_x::AbstractVector,
    pixel_edges_y::AbstractVector,
    emitter::AbstractEmitter; 
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

Integrate PSF intensity over camera pixels with optional support region optimization.

For each pixel in the specified region, numerically integrates the PSF intensity using the specified  sampling density. Physical coordinates are relative to camera with (0,0) at top-left corner. Automatically handles z-coordinate if both PSF and emitter support it.

# Arguments

  * `psf::AbstractPSF`: Point spread function to integrate
  * `pixel_edges_x::AbstractVector`: X-coordinate edges of pixels in microns
  * `pixel_edges_y::AbstractVector`: Y-coordinate edges of pixels in microns
  * `emitter::AbstractEmitter`: Emitter with position in microns relative to camera
  * `support`: Region to calculate (default: Inf = full image)

      * If Real: radius in microns around emitter
      * If Tuple: explicit (x*min, x*max, y*min, y*max) in microns
  * `sampling::Integer=2`: Number of samples per pixel in each dimension
  * `threaded::Bool=true`: Whether to use multi-threading for integration Set to false when using with automatic differentiation frameworks

# Returns

  * `Matrix{T}`: Integrated intensities where T matches emitter.photons type
  * Array is indexed as [y,x] with [1,1] at top-left pixel
  * Values represent actual photon counts in each pixel based on emitter's photon value

# Examples

```julia
# Create pixel edges for a 20x20 camera with 100nm pixels
pixel_edges_x = pixel_edges_y = 0:0.1:2.0
emitter = Emitter2D(1.0, 1.0, 1000.0)  # Emitter at (1μm, 1μm) with 1000 photons
psf = GaussianPSF(0.15)  # σ = 150nm

# Calculate over full image
pixels = integrate_pixels(psf, pixel_edges_x, pixel_edges_y, emitter)

# Calculate only within a 0.5μm radius of the emitter
pixels_roi = integrate_pixels(psf, pixel_edges_x, pixel_edges_y, emitter, support=0.5)
```

See also: [`integrate_pixels_amplitude`](@ref), [`AbstractPSF`](@ref)
