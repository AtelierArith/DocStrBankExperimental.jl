```
ones_like(x, [element_type=eltype(x)], [dims=size(x)]))
```

Create an array with the given element type and size, based upon the given source array `x`. All element of the new array will be set to 1.  The second and third arguments are both optional, defaulting to the given array's eltype and size. The dimensions may be specified as an integer or as a tuple argument.

See also [`zeros_like`](@ref) and [`fill_like`](@ref).

# Examples

```julia-repl
julia> x = rand(Float32, 2)
2-element Vector{Float32}:
 0.8621633
 0.5158395

julia> ones_like(x, (3, 3))
3×3 Matrix{Float32}:
 1.0  1.0  1.0
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> using CUDA

julia> x = CUDA.rand(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 0.82297   0.656143
 0.701828  0.391335

julia> ones_like(x, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 1.0  1.0
 1.0  1.0
```
