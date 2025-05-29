```
BoundaryConditionCoupled(other_semi_index, indices, uEltype, coupling_converter)
```

Boundary condition to glue two meshes together. Solution values at the boundary of another mesh will be used as boundary values. This requires the use of [`SemidiscretizationCoupled`](@ref). The other mesh is specified by `other_semi_index`, which is the index of the mesh in the tuple of semidiscretizations.

Note that the elements and nodes of the two meshes at the coupled boundary must coincide. This is currently only implemented for [`StructuredMesh`](@ref).

# Arguments

  * `other_semi_index`: the index in `SemidiscretizationCoupled` of the semidiscretization                     from which the values are copied
  * `indices::Tuple`: node/cell indices at the boundary of the mesh in the other                   semidiscretization. See examples below.
  * `uEltype::Type`: element type of solution
  * `coupling_converter::CouplingConverter`: function to call for converting the solution                                          state of one system to the other system

# Examples

```julia
# Connect the left boundary of mesh 2 to our boundary such that our positive
# boundary direction will match the positive y direction of the other boundary
BoundaryConditionCoupled(2, (:begin, :i), Float64, fun)

# Connect the same two boundaries oppositely oriented
BoundaryConditionCoupled(2, (:begin, :i_backwards), Float64, fun)

# Using this as y_neg boundary will connect `our_cells[i, 1, j]` to `other_cells[j, end-i, end]`
BoundaryConditionCoupled(2, (:j, :i_backwards, :end), Float64, fun)
```

!!! warning "Experimental code"
    This is an experimental feature and can change any time.

