```
detect_subpixel_edges!(out₁, out₂, img, f::AbstractEdgeDetectionAlgorithm, args...; kwargs...)
```

Detect edges of `img` to subpixel precision using algorithm `f`;  if left unspecified, `f` is assumed to be [`Canny`](@ref ImageEdgeDetection.Canny).

# Output

The integer components of an edge correspond to non-zero row and column entries in `out₁`. The accompanying subpixel offsets  are stored in a 2-D array `out₂` as length-2 vectors. One can recover the  subpixel coordinates by adding the subpixel offsets to the integer components.

# Examples

Just simply pass an algorithm to `detect_subpixel_edges!`:

```julia
f = Canny(spatial_scale = 1.4, thinning_algorithm = SubpixelNonmaximaSuppression())
img_edges = similar(img)
offsets = zeros(SVector{2,Float64}, axes(img))
detect_edges!(img_edges, offsets, img, f)
```

See also: [`detect_subpixel_edges`](@ref)
