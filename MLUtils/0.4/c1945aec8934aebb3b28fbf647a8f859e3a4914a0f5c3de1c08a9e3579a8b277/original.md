```
zeros_like(x, [element_type=eltype(x)], [dims=size(x)]))
```

Create an array with the given element type and size, based upon the given source array `x`. All element of the new array will be set to 0.  The second and third arguments are both optional, defaulting to the given array's eltype and size. The dimensions may be specified as an integer or as a tuple argument.

See also [`ones_like`](@ref) and [`fill_like`](@ref).

# Examples

```julia-repl
julia> x = rand(Float32, 2)
2-element Vector{Float32}:
 0.4005432
 0.36934233

julia> zeros_like(x, (3, 3))
3×3 Matrix{Float32}:
 0.0  0.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> using CUDA

julia> x = CUDA.rand(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 0.0695155  0.667979
 0.558468   0.59903

julia> zeros_like(x, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 0.0  0.0
 0.0  0.0
```
