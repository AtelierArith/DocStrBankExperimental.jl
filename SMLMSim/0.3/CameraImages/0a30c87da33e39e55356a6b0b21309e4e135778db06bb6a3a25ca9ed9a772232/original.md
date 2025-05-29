```
gen_images(smld::SMLD, psf::AbstractPSF; kwargs...) -> Array{T, 3} where T<:Real
```

Generate camera images from SMLD data using the specified PSF model.

# Arguments

  * `smld::SMLD`: Single molecule localization data container
  * `psf::AbstractPSF`: Point spread function model

# Keyword arguments

  * `dataset::Int=1`: Dataset number to use from SMLD
  * `frames=nothing`: Specific frames to generate (default: all frames in smld.n_frames)
  * `support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}}=Inf`: PSF support region size:

      * `Inf` (default): Calculate PSF over the entire image (most accurate but slowest)
      * `Real`: Circular region with specified radius (in microns) around each emitter
      * `Tuple{<:Real,<:Real,<:Real,<:Real}`: Explicit region as (xmin, xmax, ymin, ymax) in microns
  * `sampling::Int=2`: Supersampling factor for PSF integration
  * `threaded::Bool=true`: Enable multithreading for faster computation
  * `bg::Float64=0.0`: Background signal level (photons per pixel)
  * `poisson_noise::Bool=false`: Apply Poisson noise
  * `camera_noise::Bool=false`: Apply camera read noise (Note: This feature is not yet implemented)

# Returns

  * 3D array of camera images with dimensions [height, width, num_frames]
  * The element type T matches the type of emitter.photons (typically Float64)

# Performance Note

For the `support` parameter, using a finite radius (typically 3-5× the PSF width)  provides a good balance between accuracy and performance. For example, with a PSF width of 0.15μm, a support radius of 0.5-1.0μm is usually sufficient.
