```
struct MultiLogiset{L<:AbstractLogiset}
    modalities  :: Vector{L}
end
```

A logical dataset composed of different [modalities](https://en.wikipedia.org/wiki/Multimodal_learning)); this structure is useful for representing multimodal datasets in logical terms.

See also [`AbstractLogiset`](@ref), [`minify`](@ref).
