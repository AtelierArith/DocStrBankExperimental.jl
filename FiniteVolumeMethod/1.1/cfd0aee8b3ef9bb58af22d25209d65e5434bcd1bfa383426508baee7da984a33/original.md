```
FVMGeometry(tri::Triangulation)
```

This is a constructor for the [`FVMGeometry`](@ref) struct, which holds the mesh and associated data for the PDE.

!!! note
    It is assumed that all vertices in `tri` are in the triangulation, meaning `v` is in `tri` for each `v` in `DelaunayTriangulation.each_point_index(tri)`.


# Fields

  * `triangulation`: The underlying `Triangulation` from DelaunayTriangulation.jl.
  * `triangulation_statistics`: The statistics of the triangulation.
  * `cv_volumes::Vector{Float64}`: A `Vector` of the volumes of each control volume.
  * `triangle_props::Dict{NTuple{3,Int},TriangleProperties}`: A `Dict` mapping the indices of each triangle to its [`TriangleProperties`].
