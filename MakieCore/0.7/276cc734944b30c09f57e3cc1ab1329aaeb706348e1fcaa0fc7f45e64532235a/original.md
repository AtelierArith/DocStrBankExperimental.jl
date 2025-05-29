```
VertexGrid() <: GridBased <: ConversionTrait
```

Plots with the `VertexGrid` trait convert their input data to `(xs::Vector{Float32}, ys::Vector{Float32}, zs::Matrix{Float32})` such that `(length(xs), length(ys)) == size(zs)`, or `(xs::Matrix{Float32}, ys::Matrix{Float32}, zs::Matrix{Float32})` such that `size(xs) == size(ys) == size(zs)`.

See also: [`CellGrid`](@ref), [`ImageLike`](@ref) Used for: Surface
