```
grid(dims; periodic=false)
```

Create a $|dims|$-dimensional cubic lattice, with length `dims[i]` in dimension `i`.

### Optional Arguments

  * `periodic=false`: If true, the resulting lattice will have periodic boundary

condition in each dimension.

# Examples

```jldoctest
julia> grid([2,3])
{6, 7} undirected simple Int64 graph

julia> grid(Int8[2, 2, 2], periodic=true)
{8, 12} undirected simple Int8 graph

julia> grid((2,3))
{6, 7} undirected simple Int64 graph
```
