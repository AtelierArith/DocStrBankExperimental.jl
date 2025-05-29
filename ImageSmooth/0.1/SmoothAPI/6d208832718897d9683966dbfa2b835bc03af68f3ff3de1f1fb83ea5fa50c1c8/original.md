```
smooth!(out::GenericImage, img::GenericImage, fₛ::AbstractImageSmoothAlgorithm, args...; kwargs...)
```

Smooth `img::GenericImage` using algorithm `fₛ`

# Output

`out` will be changed in place.

# Examples

Just simply pass an algorithm to `smooth!`:

```julia
# First generate an algorithm instance
fₛ = L0Smooth()

## For Gray or RGB images
imgₛ = similar(img)

smooth!(imgₛ, img, fₛ)
```

See also: [`smooth`](@ref)
