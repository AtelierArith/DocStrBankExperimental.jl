```
VTKGridFile(filename::AbstractString, grid::AbstractGrid; kwargs...)
VTKGridFile(filename::AbstractString, dh::DofHandler; kwargs...)
```

Create a `VTKGridFile` that contains an unstructured VTK grid. The keyword arguments are forwarded to `WriteVTK.vtk_grid`, see [Data Formatting Options](https://juliavtk.github.io/WriteVTK.jl/stable/grids/syntax/#Data-formatting-options)

This file handler can be used to to write data with

  * [`write_solution`](@ref)
  * [`write_cell_data`](@ref)
  * [`write_projection`](@ref)
  * [`write_node_data`](@ref).
  * [`Ferrite.write_cellset`](@ref)
  * [`Ferrite.write_nodeset`](@ref)
  * [`Ferrite.write_constraints`](@ref)

It is necessary to call `close(::VTKGridFile)` to save the data after writing to the file handler. Using the supported `do`-block does this automatically:

```julia
VTKGridFile(filename, grid) do vtk
    write_solution(vtk, dh, u)
    write_cell_data(vtk, celldata)
end
```
