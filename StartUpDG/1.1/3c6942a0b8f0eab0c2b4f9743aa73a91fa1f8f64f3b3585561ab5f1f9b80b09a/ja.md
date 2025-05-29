```
function tag_boundary_faces(triout::TriangulateIO,
                            rd::RefElemData{2,Tri}, md::MeshData{2},
                            boundary_list::Union{NamedTuple,Dict{Symbol,Int}})
```

ここで、`boundary_list`は`TriangulateIO`メッシュ形式の境界タグの値を持つ`Dict`（または`NamedTuple`）です。出力は、`boundary_list`によって与えられたキーを持ち、その境界にある面のベクトルに等しい値を持つ`Dict`または`NamedTuple`です。

使用例：

```julia
julia> using Triangulate, StartUpDG
julia> triout = scramjet()
julia> rd = RefElemData(Tri(),N=1)
julia> md = MeshData(triangulateIO_to_VXYEToV(triout)...,rd)
julia> tag_boundary_faces(triout,rd,md, Dict(:wall=>1, :inflow=>2, :outflow=>3))
```
