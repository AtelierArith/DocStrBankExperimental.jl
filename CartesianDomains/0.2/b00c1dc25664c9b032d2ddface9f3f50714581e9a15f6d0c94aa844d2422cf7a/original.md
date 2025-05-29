```
upper_boundary_indices(domain::CartesianIndices{N}, axis::Int, n::Int) where {N}
```

Take a given CartesianIndices and extract only the upper boundary indices at an offset of `n` along a given `axis`.

# Example

```julia
julia> domain = CartesianIndices((1:10, 4:8))
CartesianIndices((1:10, 4:8))

julia> upper_boundary_indices(domain, 2, 1)
CartesianIndices((1:10, 8:8))
```
