```
ImageLike() <: ConversionTrait
```

Plots with the `ImageLike` trait convert their input data to `(xs::Interval, ys::Interval, zs::Matrix{Float32})` where xs and ys mark the limits of a quad containing zs.

See also: [`CellGrid`](@ref), [`VertexGrid`](@ref) Used for: Image
