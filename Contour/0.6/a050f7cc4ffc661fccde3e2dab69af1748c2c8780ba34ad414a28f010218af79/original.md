```
contour(x, y, z, level::Number)
contour(x, y, z, level::Number, VT::Type)
```

Trace a single contour level, indicated by the argument `level`. The extracted vertex type maybe be specified by `VT`.

You'll usually call [`lines`](@ref) on the output of `contour`, and then iterate over the result.
