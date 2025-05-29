```
get_coordinates(vtk_file::VTKFile; x_string="x", y_string="y", z_string="z")
```

Retrieve VTK coordinate vectors in each direction as a tuple of 1D vectors for a RectilinearGrid file.

Note that in VTK, points are always stored three-dimensional, even for 1D or 2D files, so you will always retrieve a tuple with three vectors.

See also: [`get_cells`](@ref)
