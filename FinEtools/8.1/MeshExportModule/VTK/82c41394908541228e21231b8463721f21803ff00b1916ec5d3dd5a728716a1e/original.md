```
vtkexportmesh(theFile::String, fens::FENodeSet, fes::T; opts...) where {T<:AbstractFESet}
```

Export mesh to a VTK 1.0 file as an unstructured grid.

Arguments:

  * `theFile` = file name,
  * `fens` = finite element node set,
  * `fes` = finite element set,
  * `opts` = keyword argument list, where

      * `scalars` = array of tuples, (name, data)
      * `vectors` = array of tuples, (name, data)

For the `scalars`: If `data` is a vector, that data is exported as a single field. On the other hand, if it is an 2d array, each column is exported  as a separate field.
