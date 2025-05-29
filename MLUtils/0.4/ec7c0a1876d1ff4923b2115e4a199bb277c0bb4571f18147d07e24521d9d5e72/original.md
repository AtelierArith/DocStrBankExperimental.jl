```
fill_like(x, val, [element_type=eltype(x)], [dims=size(x)]))
```

Create an array with the given element type and size, based upon the given source array `x`. All element of the new array will be set to `val`.  The third and fourth arguments are both optional, defaulting to the given array's eltype and size. The dimensions may be specified as an integer or as a tuple argument.

See also [`zeros_like`](@ref) and [`ones_like`](@ref).

# Examples

```julia-repl
julia> x = rand(Float32, 2)
2-element Vector{Float32}:
 0.16087806
 0.89916044

julia> fill_like(x, 1.7, (3, 3))
3×3 Matrix{Float32}:
 1.7  1.7  1.7
 1.7  1.7  1.7
 1.7  1.7  1.7

julia> using CUDA

julia> x = CUDA.rand(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 0.803167  0.476101
 0.303041  0.317581

julia> fill_like(x, 1.7, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 1.7  1.7
 1.7  1.7
```
