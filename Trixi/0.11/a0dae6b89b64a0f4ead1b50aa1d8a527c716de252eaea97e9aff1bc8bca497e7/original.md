```
T8codeMesh(meshfile::GmshFile{NDIMS}; kwargs...)
```

Main mesh constructor for the `T8codeMesh` that imports an unstructured, conforming mesh from a Gmsh mesh file (`.msh`).

# Arguments

  * `meshfile::GmshFile{NDIMS}`: Gmsh mesh file object of dimension NDIMS and give `path` to the file.

# Optional Keyword Arguments

  * `mapping`: A function of `NDIMS` variables to describe the mapping that transforms            the imported mesh to the physical domain. Use `nothing` for the identity map.
  * `polydeg::Integer`: Polynomial degree used to store the geometry of the mesh.                     The mapping will be approximated by an interpolation polynomial                     of the specified degree for each tree.                     The default of `1` creates an uncurved geometry. Use a higher value if the mapping                     will curve the imported uncurved mesh.
  * `RealT::Type`: The type that should be used for coordinates.
  * `initial_refinement_level::Integer`: Refine the mesh uniformly to this level before the simulation starts.
