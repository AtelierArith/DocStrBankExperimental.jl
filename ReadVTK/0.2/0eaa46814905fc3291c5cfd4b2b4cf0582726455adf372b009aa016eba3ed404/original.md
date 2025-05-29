```
VTKDataArray(xml_element, vtk_file)
```

Create a lightweight container for a given `xml_element` and the corresponding `vtk_file`.

The `xml_element` must be of type `DataArray` and the `vtk_file` parameter is required for retrieving the actual data. You can pass a `VTKDataArray` object to `get_data` to retrieve the actual data.

See also: [`get_data`](@ref)
