```julia
write_celldata_vtkfile!(
    vtkfile::WriteVTK.DatasetFile,
    data,
    data_name::String
) -> LightXML.XMLElement

```

Add a new cell data field with a name to an existing VTK file.
