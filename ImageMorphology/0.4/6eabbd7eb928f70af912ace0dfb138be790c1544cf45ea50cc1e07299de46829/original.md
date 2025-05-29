```
isboundary!(img::AbstractArray; background = 0, dims = coords_spatial(A), kwargs...)
```

Finds the boundaries that are just within each object, replacing the original image. `background` is the scalar value of the background pixels which will not be marked as boundaries. Keyword arguments are passed to `extreme_filter` which include `dims` indicating the dimension(s) over which to discover boundaries.

See out-of-place version, [`isboundary`](@ref), for examples.
