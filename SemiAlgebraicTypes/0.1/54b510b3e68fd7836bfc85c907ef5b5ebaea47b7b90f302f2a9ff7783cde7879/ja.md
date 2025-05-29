新しいエッジを、メッシュのエッジ配列の最後に、ポイントのインデックスの配列（番号は1から始まる）によって挿入します。

```jldoctest
julia> m = mesh(Float64);

julia> push_vertex!(m,point(0.,0.,0.)); push_vertex!(m,point(1.,0.,0.)); push_edge!(m,[1,2])
SemiAlgebraicTypes.Mesh{Float64}(Array{Float64,1}[[0.0, 0.0, 0.0], [1.0, 0.0, 0.0]], Array{Int64,1}[[1, 2]], Array{Int64,1}[], Dict{Symbol,Any}())

```
