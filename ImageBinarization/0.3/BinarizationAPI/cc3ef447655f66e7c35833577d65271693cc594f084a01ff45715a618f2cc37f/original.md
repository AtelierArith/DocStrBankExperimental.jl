```
binarize([T::Type,] img, f::AbstractImageBinarizationAlgorithm, args...; kwargs...)
```

Binarize `img` using algorithm `f`.

# Output

The return image `img₀₁` is an `Array{T}`.

If `T` is not specified, then it's inferred as `Gray{eltype(eltype(img))}`, which is `Gray{N0f8}` for img of type `Array{N0f8}` and `Array{Gray{N0f8}}`, and `Gray{Float32}` for img of type `Array{Float32}` and `Array{Gray{Float32}}`

# Examples

Just simply pass the input image and algorithm to `binarize`

```julia
img₀₁ = binarize(img, f)
```

This reads as "`binarize` image `img` using binarization algorithm `f`".

You can also explicitly specify the return type:

```julia
img₀₁_float32 = binarize(Gray{Float32}, img, f)
```

See also [`binarize!`](@ref) for in-place binarization.
