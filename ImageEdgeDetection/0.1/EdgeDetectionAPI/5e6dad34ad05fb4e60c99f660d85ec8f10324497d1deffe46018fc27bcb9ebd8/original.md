```
thin_edges([T::Type,] mag, g₁, g₂, f::AbstractEdgeThinningAlgorithm, args...; kwargs...)
```

Using algorithm `f`, thin the edge-response based on the edge magnitude `mag`, the  gradient in the first spatial dimension `g₁`, and the gradient in the second spatial dimension `g₂`.

# Output

Returns an `Array{T}` representing the thinned edge response.

If `T` is not specified, then it's inferred. Note that `T` must represent or wrap a floating point number.

# Examples

Just simply pass the input image and algorithm to `thin_edges`

```julia
using TestImages, ImageFiltering
img =  Gray.(testimage("mandril"))

# Gradient in the first and second spatial dimension
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# Gradient magnitude
mag = hypot.(g₁, g₂)

f = NonmaximaSuppression(threshold = Percentile(10))

thinned_edges = thin_edges(mag, g₁, g₂, f)
```

This reads as "`thin_edges` based on the edge response magnitude, and spatial gradients, using algorithm `f`".

You can also explicitly specify the return type:

```julia
thinned_edges_float32 = thin_edges(Gray{Float32}, mag, g₁, g₂, f)
```

See also [`thin_edges!`](@ref) for in-place edge thinning.
