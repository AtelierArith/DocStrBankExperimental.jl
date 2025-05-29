```
haloedge_regions(full_domain::CartesianIndices{N}, axis::Int, nhalo::Int) where {N}
```

Extract the halo regions along the edges of `full_domain` with a width of `nhalo`  and corresponding edge regions from the interior of the full_domain. This will create  and edge region of the same dimension as the halo region.

# Example

```julia
julia> A = [i for i in 1:10];

julia> full = CartesianIndices(A) # this is the entire "full_domain"
CartesianIndices((10,))

julia> halo, edge = haloedge_regions(full, 1, 2)
(
  halo = (lo = CartesianIndices((1:2,)), hi = CartesianIndices((9:10,))), 
  edge = (lo = CartesianIndices((3:4,)), hi = CartesianIndices((7:8,)))
)
```
