```
T8codeMesh(cmesh::Ptr{t8_cmesh},
           mapping=nothing, polydeg=1, RealT=Float64,
           initial_refinement_level=0)
```

Main mesh constructor for the `T8codeMesh` that imports an unstructured, conforming mesh from a `t8_cmesh` data structure.

# Arguments

  * `cmesh::Ptr{t8_cmesh}`: Pointer to a cmesh object.
  * `mapping`: a function of `NDIMS` variables to describe the mapping that transforms            the imported mesh to the physical domain. Use `nothing` for the identity map.
  * `polydeg::Integer`: polynomial degree used to store the geometry of the mesh.                     The mapping will be approximated by an interpolation polynomial                     of the specified degree for each tree.                     The default of `1` creates an uncurved geometry. Use a higher value if the mapping                     will curve the imported uncurved mesh.
  * `RealT::Type`: the type that should be used for coordinates.
  * `initial_refinement_level::Integer`: refine the mesh uniformly to this level before the simulation starts.
