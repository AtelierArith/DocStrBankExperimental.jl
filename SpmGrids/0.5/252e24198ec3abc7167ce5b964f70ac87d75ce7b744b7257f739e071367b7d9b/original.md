```
resize!(grid::SpmGrid, args...; kwargs...)
```

Resizes the grid in its dimensions. Arguments and keyword-arguments are similar as for the [ImageTransformations.imresize](@ref) function.

Examples:

```julia
julia> resize!(grid, ratio=0.5)  # resize all dimensions by a factor 0.5
julia> resize!(grid, ratio=(0.5, 0.5))  # resize x and y dimensions by a factor 0.5
julia> resize!(grid, ratio=(0.5, 0.5, 2.0))  # resize x and y dimensions by a factor 0.5, z dimension by a factor of 2
julia> resize!(grid, 64, 64)    # resize x and y dimensions to a specific pixelsize
julia> resize!(grid, 32, 96, 128)   # resize all dimensions to a specific pixelsize
```
