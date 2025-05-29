```
get_point_data(vtk_file::VTKFile)
```

Retrieve a lightweight `VTKData` object with the point data of the given VTK file. Only numeric data (i.e., `DataArray`) elements will be read.

See also: [`VTKData`](@ref), [`get_cell_data`](@ref), [`get_field_data`](@ref)
