```
detect_edges!([out,] img, f::AbstractEdgeDetectionAlgorithm, args...; kwargs...)
```

Detect edges of `img` using algorithm `f`;  if left unspecified, `f` is assumed to be [`Canny`](@ref ImageEdgeDetection.Canny).

# Output

If `out` is specified, it will be changed in place. Otherwise `img` will be changed in place.

# Examples

Just simply pass an algorithm to `detect_edges!`:

```julia
img_edges = similar(img)
detect_edges!(img_edges, img, f)
```

For cases you just want to change `img` in place, you don't necessarily need to manually allocate `img_edges`; just use the convenient method:

```julia
detect_edges!(img, f)
```

See also: [`detect_edges`](@ref)
