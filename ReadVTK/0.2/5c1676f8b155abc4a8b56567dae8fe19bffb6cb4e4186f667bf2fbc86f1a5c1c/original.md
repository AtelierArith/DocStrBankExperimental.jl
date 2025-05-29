```
to_meshcells(cells::VTKCells)
```

Convert a `VTKCells` object, which holds raw point and connectivity data for a number of cells, to a vector of `MeshCell` objects. The latter can, e.g., be passed to the WriteVTK.jl package for writing new VTK files. See also: [`VTKCells`](@ref), [`VTKBase.MeshCell`](@ref)
