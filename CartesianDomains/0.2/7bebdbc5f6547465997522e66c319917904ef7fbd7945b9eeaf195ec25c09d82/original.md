```
haloedge_regions(full_domain::CartesianIndices{N}, axis::Int, nhalo::Int, nedge::Int) where {N}
```

Extract the halo regions along the edges of `full_domain` with a width of `nhalo`  and corresponding edge regions of size `nedge` from the interior of the full*domain. This will  provide an edge region with a size `nedge` elements along `axis`. As an example, say you have a halo region of 2 elements, but you only want the outermost edge that is adjacent to the halo region. Calling `haloedge*regions(full_domain, 3, 2, 1)` will give you a  halo region 2 elements thick on the third axis, but the edge region will only be 1  element thick.

# Example

```julia
julia> A = [i for i in 1:10];

julia> full = CartesianIndices(A) # this is the entire "full_domain"
CartesianIndices((10,))

julia> halo, edge = haloedge_regions(full, 1, 2, 1) # this uses a halo region of 2 and edge of 1
(
  halo = (lo = CartesianIndices((1:2,)), hi = CartesianIndices((9:10,))), 
  edge = (lo = CartesianIndices((3:3,)), hi = CartesianIndices((8:8,)))
)
```
