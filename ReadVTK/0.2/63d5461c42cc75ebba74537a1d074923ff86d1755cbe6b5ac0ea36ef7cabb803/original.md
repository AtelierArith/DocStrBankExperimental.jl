```
VTKCells{Connectivity, Offsets, Types}
```

Store the `connectivity`, `offsets`, and `types` information from the VTK file as one-dimensional array-like containers. See the [VTK file format documentation](http://vtk.org/VTK/img/file-formats.pdf) for information on how to connect the `connectivity` and `offset` arrays to the actual geometric points.

You may use `length` to determine the number of cells from a `VTKCells` object.

See also: [`get_points`](@ref)
