```
get_points(vtk_file::VTKFile)
```

Retrieve VTK points as a two-dimensional array-like container.

The points are stored in dimension × points format. Note that in VTK, points are always stored three-dimensional, even for 1D or 2D files.

See also: [`get_cells`](@ref)
