```
PointMeshBlockHeader{T,N}
```

A mesh defines the locations at which variables are defined. Since the geometry of a problem is fixed and most variables will be defined at positions relative to a fixed grid, it makes sense to write this position data once in its own block. Each variable will then refer to one of these mesh blocks to provide their location data.

The `PointMeshBlockHeader` is used for representing the positions at which vector field discretizations are defined. The block header contains the `base_header` (a `BlockHeader`) and the following metadata

  * `mults`: The normalisation factor applied to the grid data

in each direction.

  * `labels`: The axis labels for this grid in each direction.
  * `units`: The units for this grid in each direction after the

normalisation factors have been applied.

  * `geometry`: The geometry of the block.
  * `minval`: The minimum coordinate values in each direction.
  * `maxval`: The maximum coordinate values in each direction.
  * `np`: The number of points.

The geometry of the block can take the following values

  * `Null`: Unspecified geometry. This is an error.
  * `Cartesian`: Cartesian geometry.
  * `Cylindrical`: Cylindrical geometry.
  * `Spherical`: Spherical geometry.

The data written is the locations of each point in the first direction followed by the locations in the second direction and so on. Thus, for a 3d simulation, if we define the first point as having coordinates $(x_1; y_1; x_1)$ and the second point as $(x_2; y_2; z_2)$, etc. then the data written to file is a 1d array with  elements $(x_1; x_2; \dots; x_{np})$, followed by the array $(y_1; y_2; \dots; y_{np})$ and finally the array $(z_1; z_2; \dots; z_{np})$ where $np$ corresponds to the number of points in the mesh. For a 1d simulation, only the x array is written and for a 2d simulation only the x and y arrays are written.
