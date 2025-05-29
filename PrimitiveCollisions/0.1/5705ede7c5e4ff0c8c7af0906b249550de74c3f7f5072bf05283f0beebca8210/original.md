```julia
struct Rect{R<:Real} <: AbstractPolygon{2}
```

A 2-dimensional rectangle which stores its half-extents (`half_ext`) in both dimensions.
