```
get_cell_data(pvtk_file::PVTKFile)
```

Retrieve a lightweight vector with `PVTKData` objects with the cell data of the given PVTK files. Only numeric data (i.e., `DataArray`) elements will be read.

See also: [`PVTKData`](@ref), [`get_point_data`](@ref), [`get_field_data`](@ref)
