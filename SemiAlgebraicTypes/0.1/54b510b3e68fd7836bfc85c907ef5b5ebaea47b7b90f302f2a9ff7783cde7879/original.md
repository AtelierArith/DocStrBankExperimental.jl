Insert a new edge given by the array of indices of the points (numbering starting at 1) at the end of the edge array of the mesh.

```jldoctest
julia> m = mesh(Float64);

julia> push_vertex!(m,point(0.,0.,0.)); push_vertex!(m,point(1.,0.,0.)); push_edge!(m,[1,2])
SemiAlgebraicTypes.Mesh{Float64}(Array{Float64,1}[[0.0, 0.0, 0.0], [1.0, 0.0, 0.0]], Array{Int64,1}[[1, 2]], Array{Int64,1}[], Dict{Symbol,Any}())

```
