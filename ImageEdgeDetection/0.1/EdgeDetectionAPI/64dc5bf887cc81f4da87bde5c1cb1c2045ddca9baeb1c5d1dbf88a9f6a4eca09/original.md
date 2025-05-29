```
thin_subpixel_edges!(out₁, out₂, mag, g₁, g₂, f::AbstractEdgeThinningAlgorithm, args...; kwargs...)
```

Isolate local maxima of gradient magnitude `mag` along the local gradient direction. The arguments `g₁` and `g₂` represent the  gradient in the first spatial dimension (y), and the second spatial dimension (x), respectively.

# Output

The integer components of the local maxima correspond to non-zero row and column entries in `out₁`. The accompanying subpixel offsets  are stored in a 2-D array `out₂` as length-2 vectors. One can recover the  subpixel coordinates by adding the subpixel offsets to the integer components.

# Examples

Just simply pass an algorithm to `thin_subpixel_edges!`:

```julia
using TestImages, ImageFiltering
img =  Gray.(testimage("mandril"))

# Gradient in the first and second spatial dimension
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# Gradient magnitude
mag = hypot.(g₁, g₂)

f = SubpixelNonmaximaSuppression(threshold = Percentile(10))

thinned_edges = zeros(eltype(mag), axes(mag))
offsets = zeros(SVector{2,Float64}, axes(mag))
thin_subpixel_edges!(thinned_edges, offsets, mag, g₁, g₂, f)
```

See also: [`thin_subpixel_edges`](@ref)
