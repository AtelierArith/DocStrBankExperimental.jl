メッシュの頂点配列の末尾に頂点を挿入します。

```jldoctest
julia> m = mesh(Float64,3);

julia> push_vertex!(m,[1.,2.,3.])
SemiAlgebraicTypes.Mesh{Float64}(Array{Float64,1}[[1.0, 2.0, 3.0]], Array{Int64,1}[], Array{Int64,1}[], Dict{Symbol,Any}())

```
