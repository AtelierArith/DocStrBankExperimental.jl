```
rand_like([rng=default_rng()], x, [element_type=eltype(x)], [dims=size(x)])
```

Create an array with the given element type and size, based upon the given source array `x`. All element of the new array will be set to a random value. The last two arguments are both optional, defaulting to the given array's eltype and size. The dimensions may be specified as an integer or as a tuple argument.

The default random number generator is used, unless a custom one is passed in explicitly as the first argument.

See also `Base.rand` and [`randn_like`](@ref).

# Examples

```julia-repl
julia> x = ones(Float32, 2)
2-element Vector{Float32}:
 1.0
 1.0

julia> rand_like(x, (3, 3))
3×3 Matrix{Float32}:
 0.780032  0.920552  0.53689
 0.121451  0.741334  0.5449
 0.55348   0.138136  0.556404

julia> using CUDA

julia> CUDA.ones(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 1.0  1.0
 1.0  1.0

julia> rand_like(x, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 0.429274  0.135379
 0.718895  0.0098756
```
