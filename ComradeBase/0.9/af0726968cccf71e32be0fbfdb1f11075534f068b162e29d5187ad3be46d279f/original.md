```julia
struct IntensityMap{T, N, D, G<:(ComradeBase.AbstractRectiGrid{D}), A<:AbstractArray{T, N}, R<:Tuple, Na} <: DimensionalData.AbstractDimArray{T, N, D, A<:AbstractArray{T, N}}
```

This type is the basic array type for all images and models that obey the `ComradeBase` interface. The type is a subtype of `DimensionalData.AbstractDimArray` however, we make a few changes to support the Comrade API.

1. The dimensions should be specified by an `AbstractRectiGrid` interface. Usually users just need the [`RectiGrid`](@ref) grid, for rectilinear grids.
2. There are two ways to access the dimensions of the array. `dims(img)` will return the usual `DimArray` dimensions, i.e. a `Tuple{DimensionalData.Dim, ...}`. The other way to access the array dimensions is using the `getproperty`, e.g., `img.X` will return the RA/X grid locations but stripped of the usual `DimensionalData.Dimension` material. This `getproperty` behavior is *NOT CONSIDERED** part of the stable API and may be changed in the future.
3. Metadata is stored in the `AbstractRectiGrid` type through the `header` property and can be accessed through `metadata` or `header`

The most common way to create a `IntensityMap` is to use the function definitions

```julia-repl
julia> g = imagepixels(10.0, 10.0, 128, 128; header=NoHeader())
julia> X = g.X; Y = g.Y
julia> data = rand(128, 128)
julia> img1 = IntensityMap(data, g)
julia> img2 = IntensityMap(data, (;X, Y); header=header(g))
julia> img1 == img2
true
julia> img3 = IntensityMap(data, 10.0, 10.0; header=NoHeader())
```

Broadcasting, map, and reductions should all just obey the `DimensionalData` interface.
