```
generate_downsample(num_dim, downsample_dims, factor)
```

Generate a function (based on Tullio.jl) which can be used to downsample arrays. `num_dim` (Integer) are the dimensions of the array. `downsample_dims` is a list of which dimensions should be downsampled. `factor` is a downsampling factor. It needs to be an integer number.

# Examples

```jldoctest
julia> ds = generate_downsample(2, [1, 2], 2) 
[...]
julia> ds([1 2; 3 4; 5 6; 7 8])
2×1 Array{Float64,2}:
 2.5
 6.5

julia> ds = generate_downsample(2, [1], 2)
[...]
julia> ds([1 2; 3 5; 5 6; 7 8])
2×2 Array{Float64,2}:
 2.0  3.5
 6.0  7.0
```
