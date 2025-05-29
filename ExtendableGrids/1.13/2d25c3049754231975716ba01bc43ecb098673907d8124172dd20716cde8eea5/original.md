```julia
simplexgrid(
    file::String;
    format,
    kwargs...
) -> ExtendableGrids.ExtendableGrid{Float64, Int32}

```

Read grid from file.  Supported formats:

  * "*.sg": pdelib sg files. Format versions:

      * `format=v"2.0"`:  long version with some unnecessary data
      * `format=v"2.1"`: shortened version only with cells, cellnodes, cellregions, bfacenodes, bfaceregions
      * `format=v"2.2"`: like 2.1, but additional info on cell and node partitioning. Edge partitioning is not stored in the file and may be re-established by [`induce_edge_partitioning!`](@ref).
  * "*.geo": gmsh geometry description (requires `using Gmsh`)
  * "*.msh": gmsh mesh (requires `using Gmsh`)
