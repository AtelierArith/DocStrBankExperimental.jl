```
VTKFile
```

Hold all relevant information about a VTK XML file that has been read in.

# Fields

  * `filename`: original path to the VTK file that has been read in
  * `xml_file`: object that represents the XML file
  * `file_type`: currently only `"UnstructuredGrid"` or `"ImageData"` are supported
  * `version`: VTK XML file format version
  * `byte_order`: can be `LittleEndian` or `BigEndian` and must currently be the same as the system's
  * `compressor`: can be empty (no compression) or `vtkZLibDataCompressor`
  * `appended_data`: in case of appended data (see XML documentation), the data is stored here for                  convenient retrieval (otherwise it is empty)
  * `n_points`: number of points in the VTK file
  * `n_cells`: number of cells in the VTK file`
