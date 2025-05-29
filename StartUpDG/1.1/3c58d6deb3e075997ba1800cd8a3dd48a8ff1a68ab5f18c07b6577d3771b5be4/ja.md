```
function tag_boundary_faces(md, boundary_name::Symbol = :entire_boundary)
function tag_boundary_faces(md, boundary_list::Dict{Symbol, <:Function})
```

引数なしで呼び出すと、`Dict(:entire_boundary => boundary_faces)`を返します。

使用例:

```julia
julia> rd = RefElemData(Tri(), N=1)
julia> md = MeshData(uniform_mesh(Tri(), 2)..., rd)
julia> on_bottom_boundary(x, y, tol = 1e-13) = abs(y+1) < tol
julia> on_top_boundary(x, y, tol = 1e-13) = abs(y-1) < tol
julia> tag_boundary_faces(Dict(:bottom => on_bottom_boundary,
                               :top    => on_top_boundary), md)
```
