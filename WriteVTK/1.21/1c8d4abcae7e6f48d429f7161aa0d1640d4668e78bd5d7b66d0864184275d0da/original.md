```
vtk_write_array(filename, arrays, labels)
vtk_write_array(filename, array; label = "array")
```

Write Julia arrays to a VTK image data file (.vti).

Useful for general visualisation of arrays. The input can be a 2D or 3D array.

Multiple arrays can be given as a tuple. For instance,

```
vtk_write_array(filename, (u, v), ("u", "v"))
```

In that case, the arrays must have the same dimensions.
