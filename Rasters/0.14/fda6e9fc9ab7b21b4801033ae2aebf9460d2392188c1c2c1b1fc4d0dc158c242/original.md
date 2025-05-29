```
AbstractRasterSeries <: DimensionalData.AbstractDimensionalArray
```

Abstract supertype for high-level `DimensionalArray` that hold `RasterStacks`, `Rasters`, or the paths they can be loaded from. `RasterSeries` are indexed with dimensions as with a `AbstractRaster`. This is useful when you have multiple files containing rasters or stacks of rasters spread over dimensions like time and elevation.

As much as possible, implementations should facilitate loading entire directories and detecting the dimensions from metadata.

This allows syntax like below for a series of stacks of arrays:

```julia
RasterSeries[Time(Near(DateTime(2001, 1))][:temp][Y(Between(70, 150)), X(Between(-20,20))] |> plot`
```

[`RasterSeries`](@ref) is the concrete implementation.
