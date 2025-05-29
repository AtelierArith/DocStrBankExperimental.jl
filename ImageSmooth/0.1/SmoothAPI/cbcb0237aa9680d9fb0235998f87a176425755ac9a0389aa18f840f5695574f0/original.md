```
smooth(img, fₛ::AbstractImageSmoothAlgorithm, args...; kwargs...)
```

Smooth `img` using algorithm `fₛ`

# Output

The return image `imgₛ` is an `Array{Gray{N0f8}} for`Gray`image, and`Array{RGB{N0f8}}`for`RGB` image.

# Examples

Just simply pass the input image and algorithm to `smooth`

```julia
fₛ = L0Smooth()

imgₛ = smooth(img, fₛ)
```

This reads as "`smooth` image `img` using smoothing algorithm `fₛ`".

See also [`smooth!`](@ref) for in-place smoothing.
