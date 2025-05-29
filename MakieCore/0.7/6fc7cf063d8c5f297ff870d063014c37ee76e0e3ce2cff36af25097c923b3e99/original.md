```
CellGrid() <: GridBased <: ConversionTrait
```

Plots with the `CellGrid` trait convert their input data to `(xs::Vector{Float32}, ys::Vector{Float32}, zs::Matrix{Float32})` such that `(length(xs), length(ys)) == size(zs) .+ 1`. After the conversion the x and y values represent the edges of cells corresponding to z values.

See also: [`VertexGrid`](@ref), [`ImageLike`](@ref) Used for: Heatmap
