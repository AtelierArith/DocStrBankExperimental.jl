```
get_coordinate_data(pvtk_file::PVTKFile)
```

Retrieve a lightweight `{VTKData` object with the coordinate data of the given VTK file. Only coordinates of numeric data (i.e., `DataArray`) elements will be read.

See also: [`PVTKData`](@ref), [`get_point_data`](@ref), [`get_cell_data`](@ref), [`get_field_data`](@ref)
