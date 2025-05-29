```
out = detect_edges([T::Type,] img, f::AbstractEdgeDetectionAlgorithm, args...; kwargs...)
```

Detect edges of `img` using algorithm `f`;  if left unspecified, `f` is assumed to be [`Canny`](@ref ImageEdgeDetection.Canny).

# Output

The return image `out` is an `Array{T}`. If `T` is not specified, then it's inferred.

# Examples

Just simply pass the input image and algorithm to `detect_edges`

```julia
f = Canny(spatial_scale = 1.4)
img_edges = detect_edges(img, f)
```

This reads as "`detect_edges` of image `img` using algorithm `f`".

You can also explicitly specify the return type:

```julia
f = Canny(spatial_scale = 1.4)
img_edges_float32 = detect_edges(Gray{Float32}, img, f)
```

See also [`detect_edges!`](@ref) for in-place edge detection.
