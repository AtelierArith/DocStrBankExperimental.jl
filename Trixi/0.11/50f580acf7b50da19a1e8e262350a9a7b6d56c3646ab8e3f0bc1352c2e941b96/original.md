```
T8codeMesh(meshfile::AbaqusFile{NDIMS};
           mapping=nothing, polydeg=1, RealT=Float64,
           initial_refinement_level=0, unsaved_changes=true,
           boundary_symbols = nothing)
```

Main mesh constructor for the `T8codeMesh` that imports an unstructured, conforming mesh from an Abaqus mesh file (`.inp`).

To create a curved unstructured `T8codeMesh` two strategies are available:

  * `HOHQMesh Abaqus`: High-order, curved boundary information created by                    [`HOHQMesh.jl`](https://github.com/trixi-framework/HOHQMesh.jl) is                    available in the `meshfile`. The mesh polynomial degree `polydeg`                    of the boundaries is provided from the `meshfile`. The computation of                    the mapped tree coordinates is done with transfinite interpolation                    with linear blending similar to [`UnstructuredMesh2D`](@ref). Boundary name                    information is also parsed from the `meshfile` such that different boundary                    conditions can be set at each named boundary on a given tree.
  * `Standard Abaqus`: By default, with `mapping=nothing` and `polydeg=1`, this creates a                    straight-sided mesh from the information parsed from the `meshfile`. If a mapping                    function is specified then it computes the mapped tree coordinates via polynomial                    interpolants with degree `polydeg`. The mesh created by this function will only                    have one boundary `:all` if `boundary_symbols` is not specified.                    If `boundary_symbols` is specified the mesh file will be parsed for nodesets defining                    the boundary nodes from which boundary edges (2D) and faces (3D) will be assigned.

Note that the `mapping` and `polydeg` keyword arguments are only used by the `HOHQMesh Abaqus` option. The `Standard Abaqus` routine obtains the mesh `polydeg` directly from the `meshfile` and constructs the transfinite mapping internally.

The particular strategy is selected according to the header present in the `meshfile` where the constructor checks whether or not the `meshfile` was created with [HOHQMesh.jl](https://github.com/trixi-framework/HOHQMesh.jl). If the Abaqus file header is not present in the `meshfile` then the `T8codeMesh` is created by `Standard Abaqus`.

The default keyword argument `initial_refinement_level=0` corresponds to a forest where the number of trees is the same as the number of elements in the original `meshfile`. Increasing the `initial_refinement_level` allows one to uniformly refine the base mesh given in the `meshfile` to create a forest with more trees before the simulation begins. For example, if a two-dimensional base mesh contains 25 elements then setting `initial_refinement_level=1` creates an initial forest of `2^2 * 25 = 100` trees.

# Arguments

  * `meshfile::AbaqusFile{NDIMS}`: Abaqus mesh file object of dimension NDIMS and given `path` to the file.

# Optional Keyword Arguments

  * `mapping`: A function of `NDIMS` variables to describe the mapping that transforms            the imported mesh to the physical domain. Use `nothing` for the identity map.
  * `polydeg::Integer`: Polynomial degree used to store the geometry of the mesh.                     The mapping will be approximated by an interpolation polynomial                     of the specified degree for each tree.                     The default of `1` creates an uncurved geometry. Use a higher value if the mapping                     will curve the imported uncurved mesh.
  * `RealT::Type`: The type that should be used for coordinates.
  * `initial_refinement_level::Integer`: Refine the mesh uniformly to this level before the simulation starts.
  * `boundary_symbols::Vector{Symbol}`: A vector of symbols that correspond to the boundary names in the `meshfile`.                                     If `nothing` is passed then all boundaries are named `:all`.
