```
vtkexportmesh(theFile::String, Connectivity, Points, Cell_type;
    vectors=nothing, scalars=nothing)
```

Export mesh to a VTK 1.0 file as an unstructured grid.

Arguments:

  * `theFile` = file name,
  * `Connectivity` = array of connectivities, one row per element,
  * `Points` = array of node coordinates, one row per node,
  * `Cell_type` = type of the cell, refer to the predefined constants P1, L2, ..., H20, ...
  * `scalars` = array of tuples, (name, data)
  * `vectors` = array of tuples, (name, data)

For the `scalars`: If `data` is a vector, that data is exported as a single field. On the other hand, if it is an 2d array, each column is exported  as a separate field.
