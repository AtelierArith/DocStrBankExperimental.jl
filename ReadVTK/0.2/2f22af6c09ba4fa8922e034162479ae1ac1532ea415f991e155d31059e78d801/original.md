```
get_cell_data(vtk_file::VTKFile)
```

Retrieve a lightweight `VTKData` object with the cell data of the given VTK file. Only numeric data (i.e., `DataArray`) elements will be read.

See also: [`VTKData`](@ref), [`get_point_data`](@ref), [`get_field_data`](@ref)
