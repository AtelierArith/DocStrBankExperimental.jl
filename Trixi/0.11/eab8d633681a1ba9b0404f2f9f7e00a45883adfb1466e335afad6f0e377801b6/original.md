```
T8codeMesh(filepath::String, NDIMS; kwargs...)
```

Main mesh constructor for the `T8codeMesh` that imports an unstructured, conforming mesh from either a Gmsh mesh file (`.msh`) or Abaqus mesh file  (`.inp`) which is determined by the file extension.

# Arguments

  * `filepath::String`: path to a Gmsh or Abaqus mesh file.
  * `ndims`: Mesh file dimension: `2` or `3`.

# Optional Keyword Arguments

  * `mapping`: A function of `NDIMS` variables to describe the mapping that transforms            the imported mesh to the physical domain. Use `nothing` for the identity map.
  * `polydeg::Integer`: Polynomial degree used to store the geometry of the mesh.                     The mapping will be approximated by an interpolation polynomial                     of the specified degree for each tree.                     The default of `1` creates an uncurved geometry. Use a higher value if the mapping                     will curve the imported uncurved mesh.
  * `RealT::Type`: The type that should be used for coordinates.
  * `initial_refinement_level::Integer`: Refine the mesh uniformly to this level before the simulation starts.
