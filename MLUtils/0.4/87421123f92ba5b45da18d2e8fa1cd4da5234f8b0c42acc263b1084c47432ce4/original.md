```
randn_like([rng=default_rng()], x, [element_type=eltype(x)], [dims=size(x)])
```

Create an array with the given element type and size, based upon the given source array `x`. All element of the new array will be set to a random value drawn from a normal distribution. The last two arguments are both optional, defaulting to the given array's eltype and size. The dimensions may be specified as an integer or as a tuple argument.

The default random number generator is used, unless a custom one is passed in explicitly as the first argument.

See also `Base.randn` and [`rand_like`](@ref).

# Examples

```julia-repl
julia> x = ones(Float32, 2)
2-element Vector{Float32}:
 1.0
 1.0

julia> randn_like(x, (3, 3))
3×3 Matrix{Float32}:
 -0.385331    0.956231   0.0745102
  1.43756    -0.967328   2.06311
  0.0482372   1.78728   -0.902547

julia> using CUDA

julia> CUDA.ones(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 1.0  1.0
 1.0  1.0

julia> randn_like(x, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 -0.578527   0.823445
 -1.01338   -0.612053
```
