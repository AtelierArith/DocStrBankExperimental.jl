Randomize image phase leaving amplitude spectrum unchanged.

```
Usage:   newimg = nophase(img)

Argument:       img::AbstractArray{T,2} where T <: Real - Input image

Returns:     newimg::Array{Float64,2} - Image with randomized phase
```

In general most images will be destroyed by this transform.  However, some textures are reproduced in an 'amplitude only' image quite well.  Typically these are textures which have an amplitude spectrum that have a limited number of isolated peaks. That is, a texture made up from a limited number of strong harmonics.

See also: [`noiseonf`](@ref), [`quantizephase`](@ref), [`swapphase`](@ref)
