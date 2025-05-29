```
out₁, out₂ = detect_subpixel_edges([T₁::Type, T₂::Type], img, f::AbstractEdgeDetectionAlgorithm, args...; kwargs...)
```

Detect edges of `img` to subpixel precision using algorithm `f`;  if left unspecified, `f` is assumed to be [`Canny`](@ref ImageEdgeDetection.Canny).

# Output

The integer components of an edge correspond to non-zero row and column entries in `out₁` which is an `Array{T₁}`. The accompanying subpixel offsets  are stored in a 2-D array `out₂` as length-2 vectors (`Array{SVector{2, T₂}}`). One can recover the  subpixel coordinates by adding the subpixel offsets to the integer components.

# Examples

Just simply pass the input image and algorithm to `detect_subpixel_edges`

```julia
f = Canny(spatial_scale = 1.4, thinning_algorithm = SubpixelNonmaximaSuppression())
img_edges, offsets = detect_subpixel_edges(img, f)
```

This reads as "`detect_subpixel_edges` of image `img` using algorithm `f`".

You can also explicitly specify the return types:

```julia
f = Canny(spatial_scale = 1.4, thinning_algorithm = SubpixelNonmaximaSuppression())
img_edges, offsets = detect_subpixel_edges(Gray{Float32}, Float32, img, f)
```

See also [`detect_subpixel_edges!`](@ref) for in-place edge detection.
