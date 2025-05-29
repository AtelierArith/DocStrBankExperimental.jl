```
VTKDataArray{T, N, Format}
```

Hold information about a single VTK data array (cell data or point data).

The data type is encoded as `T`, `N` represents the size of the second dimension in case of multi-dimensonal arrays (or `1` for a vector), and `Format` encodes in which format the data is stored in the XML file.

The actual data can be retrieved by calling `get_data` on the `PVTKDataArray` object.

See also: [`get_data`](@ref)
