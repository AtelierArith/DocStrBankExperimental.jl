```
P4estMesh(trees_per_dimension; polydeg,
          mapping=nothing, faces=nothing, coordinates_min=nothing, coordinates_max=nothing,
          RealT=Float64, initial_refinement_level=0, periodicity=true, unsaved_changes=true,
          p4est_partition_allow_for_coarsening=true)
```

Create a structured curved/higher-order `P4estMesh` of the specified size.

There are three ways to map the mesh to the physical domain.

1. Define a `mapping` that maps the hypercube `[-1, 1]^n`.
2. Specify a `Tuple` `faces` of functions that parametrize each face.
3. Create a rectangular mesh by specifying `coordinates_min` and `coordinates_max`.

Non-periodic boundaries will be called `:x_neg`, `:x_pos`, `:y_neg`, `:y_pos`, `:z_neg`, `:z_pos`.

# Arguments

  * `trees_per_dimension::NTupleE{NDIMS, Int}`: the number of trees in each dimension.
  * `polydeg::Integer`: polynomial degree used to store the geometry of the mesh.                     The mapping will be approximated by an interpolation polynomial                     of the specified degree for each tree.
  * `mapping`: a function of `NDIMS` variables to describe the mapping that transforms            the reference mesh (`[-1, 1]^n`) to the physical domain.            Use only one of `mapping`, `faces` and `coordinates_min`/`coordinates_max`.
  * `faces::NTuple{2*NDIMS}`: a tuple of `2 * NDIMS` functions that describe the faces of the domain.                           Each function must take `NDIMS-1` arguments.                           `faces[1]` describes the face onto which the face in negative x-direction                           of the unit hypercube is mapped. The face in positive x-direction of                           the unit hypercube will be mapped onto the face described by `faces[2]`.                           `faces[3:4]` describe the faces in positive and negative y-direction respectively                           (in 2D and 3D).                           `faces[5:6]` describe the faces in positive and negative z-direction respectively (in 3D).                           Use only one of `mapping`, `faces` and `coordinates_min`/`coordinates_max`.
  * `coordinates_min`: vector or tuple of the coordinates of the corner in the negative direction of each dimension                    to create a rectangular mesh.                    Use only one of `mapping`, `faces` and `coordinates_min`/`coordinates_max`.
  * `coordinates_max`: vector or tuple of the coordinates of the corner in the positive direction of each dimension                    to create a rectangular mesh.                    Use only one of `mapping`, `faces` and `coordinates_min`/`coordinates_max`.
  * `RealT::Type`: the type that should be used for coordinates.
  * `initial_refinement_level::Integer`: refine the mesh uniformly to this level before the simulation starts.
  * `periodicity`: either a `Bool` deciding if all of the boundaries are periodic or an `NTuple{NDIMS, Bool}`                deciding for each dimension if the boundaries in this dimension are periodic.
  * `unsaved_changes::Bool`: if set to `true`, the mesh will be saved to a mesh file.
  * `p4est_partition_allow_for_coarsening::Bool`: Must be `true` when using AMR to make mesh adaptivity                                               independent of domain partitioning. Should be `false` for static meshes                                               to permit more fine-grained partitioning.
