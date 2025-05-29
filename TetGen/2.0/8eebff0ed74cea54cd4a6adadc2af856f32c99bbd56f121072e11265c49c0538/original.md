```julia
tetrahedralize(mesh; ...)
tetrahedralize(mesh, command; marker, holes)

```

Tetrahedralize a mesh of polygons with optional facet markers. Returns a mesh of tetrahdra. 

With `GeometryBasics` version 0.4, the input mesh has to be a `GeometryBasics.Mesh` with possible metadata. With `GeometryBasics` version 0.5, the input mesh has to be a `GeometryBasics.MetaMesh`.

Default command is "Qp", creating the Delaunay triangulation of the point set. See the list of possible flags in the documentation of [`tetrahedralize(::RawTetGenIO, flags)`](@ref).
