```
gen_image(smld::SMLD, psf::AbstractPSF, frame::Int; kwargs...) -> Matrix{T} where T<:Real
```

Generate a single camera image for a specific frame from SMLD data. See `gen_images` for full documentation of parameters.

# Returns

  * A 2D camera image as Matrix{T} where T matches the type of emitter.photons
