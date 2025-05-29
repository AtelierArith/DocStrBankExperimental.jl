```
T8codeMesh{NDIMS, RealT}(forest, boundary_names; polydeg = 1, mapping = nothing)
```

Main mesh constructor for the `T8codeMesh` wrapping around a given t8code `forest` object. This constructor is typically called by other `T8codeMesh` constructors.

# Arguments

  * `forest`: Pointer to a t8code forest.
  * `boundary_names`: List of boundary names.
  * `polydeg::Integer`: Polynomial degree used to store the geometry of the mesh.                     The mapping will be approximated by an interpolation polynomial                     of the specified degree for each tree.
  * `mapping`: A function of `NDIMS` variables to describe the mapping that transforms            the imported mesh to the physical domain. Use `nothing` for the identity map.
