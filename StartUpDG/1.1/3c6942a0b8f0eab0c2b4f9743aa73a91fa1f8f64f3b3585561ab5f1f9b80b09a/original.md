```
function tag_boundary_faces(triout::TriangulateIO,
                            rd::RefElemData{2,Tri}, md::MeshData{2},
                            boundary_list::Union{NamedTuple,Dict{Symbol,Int}})
```

Here, `boundary_list` is a `Dict` (or `NamedTuple`) whose values are the boundary tags for a `TriangulateIO` mesh format. The output is a `Dict` or `NamedTuple` with keys given by `boundary_list` and `values` equal to vectors of faces on that given boundary.

Example usage:

```julia
julia> using Triangulate, StartUpDG
julia> triout = scramjet()
julia> rd = RefElemData(Tri(),N=1)
julia> md = MeshData(triangulateIO_to_VXYEToV(triout)...,rd)
julia> tag_boundary_faces(triout,rd,md, Dict(:wall=>1, :inflow=>2, :outflow=>3))
```
