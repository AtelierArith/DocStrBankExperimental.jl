```
AbstractRasterStack
```

Abstract supertype for objects that hold multiple [`AbstractRaster`](@ref)s that share spatial dimensions.

They are `NamedTuple`-like structures that may either contain `NamedTuple` of [`AbstractRaster`](@ref)s, string paths that will load [`AbstractRaster`](@ref)s, or a single path that points to a file containing multiple layers, like NetCDF or HDF5. Use and syntax is similar or identical for all cases.

`AbstractRasterStack` can hold layers that share some or all of their dimensions. They cannot have the same dimension with different length or spatial extent as another layer.

`getindex` on an `AbstractRasterStack` generally returns a memory backed standard [`Raster`](@ref). `raster[:somelayer] |> plot` plots the layers array, while `raster[:somelayer, X(1:100), Band(2)] |> plot` will plot the subset without loading the whole array.

`getindex` on an `AbstractRasterStack` with a key returns another stack with `getindex` applied to all the arrays in the stack.
