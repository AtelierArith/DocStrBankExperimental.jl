```
thin_edges!([out,] mag, g₁, g₂, f::AbstractEdgeThinningAlgorithm, args...; kwargs...)
```

Isolate local maxima of gradient magnitude `mag` along the local gradient direction. The arguments `g₁` and `g₂` represent the  gradient in the first spatial dimension (y), and the second spatial dimension (x), respectively.

# Output

If `out` is specified, it will be changed in place. Otherwise `mag` will be changed in place.

# Examples

Just simply pass an algorithm to `thin_edges!`:

```julia
using TestImages, ImageFiltering
img =  Gray.(testimage("mandril"))

# Gradient in the first and second spatial dimension
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# Gradient magnitude
mag = hypot.(g₁, g₂)

f = SubpixelNonmaximaSuppression(threshold = Percentile(10))

thinned_edges = zeros(eltype(mag), axes(mag))
thin_edges!(thinned_edges, mag, g₁, g₂, f)
```

For cases you just want to change `mag` in place, you don't necessarily need to manually allocate `thinned_edges`; just use the convenient method:

```julia
thin_edges!(mag, g₁, g₂, f)
```

See also: [`thin_edges`](@ref)
