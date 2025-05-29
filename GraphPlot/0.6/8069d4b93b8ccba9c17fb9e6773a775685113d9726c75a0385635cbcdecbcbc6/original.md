This function is copy from [IainNZ](https://github.com/IainNZ)'s [GraphLayout.jl](https://github.com/IainNZ/GraphLayout.jl)

Position nodes in concentric circles.

**Parameters**

*g* a graph

*nlist* Vector of Vector, Vector of node Vector for each shell.

**Examples**

```
julia> g = smallgraph(:karate)
julia> nlist = Vector{Vector{Int}}()
julia> push!(nlist, collect(1:5))
julia> push!(nlist, collect(6:nv(g)))
julia> locs_x, locs_y = shell_layout(g, nlist)
```
