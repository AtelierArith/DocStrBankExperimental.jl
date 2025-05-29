```
AbstractRaster <: DimensionalData.AbstractDimArray
```

Abstract supertype for objects that wrap an array (or location of an array) and metadata about its contents. It may be memory or hold a `FileArray`, which holds the filename, and is only opened when required.

`AbstractRaster`s inherit from [`AbstractDimArray`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.AbstractDimArray) from DimensionalData.jl. They can be indexed as regular Julia arrays or with DimensionalData.jl [`Dimension`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Dimension)s. They will plot as a heatmap in Plots.jl with correct coordinates and labels, even after slicing with `getindex` or `view`. `getindex` on a `AbstractRaster` will always return a memory-backed `Raster`.
