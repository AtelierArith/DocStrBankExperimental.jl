```
lower_boundary_indices(domain::CartesianIndices{N}, axis::Int, n::Int) where {N}
```

Take a given CartesianIndices and extract only the lower boundary indices at an offset of `n` along a given `axis`.

# Example

```julia
julia> domain = CartesianIndices((1:10, 4:8))
CartesianIndices((1:10, 4:8))

julia> lower_boundary_indices(domain, 2, 0) # select the first index on axis 2
CartesianIndices((1:10, 4:4))
```
