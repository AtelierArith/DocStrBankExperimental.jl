```
VTKPrimitives{Connectivity, Offsets}
```

Store the `connectivity` and `offsets` information from the VTK PolyData file as one-dimensional array-like containers. See the [VTK file format documentation](http://vtk.org/VTK/img/file-formats.pdf) for information on how to connect the `connectivity` and `offset` arrays to the actual geometric points.

You may use `length` to determine the number of cells from a `VTKPrimitives` object.
