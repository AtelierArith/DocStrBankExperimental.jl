```
PlainMeshBlockHeader{T,N}
```

A mesh defines the locations at which variables are defined. Since the geometry of a problem is fixed and most variables will be defined at positions relative to a fixed grid, it makes sense to write this position data once in its own block. Each variable will then refer to one of these mesh blocks to provide their location data.

The `PlainMeshBlockHeader` is used for representing the positions at which scalar field discretizations are defined. The block header contains the `base_header` (a `BlockHeader`) and the following metadata

  * `mults`: The normalisation factor applied to the grid data

in each direction.

  * `labels`: The axis labels for this grid in each direction.
  * `units`: The units for this grid in each direction after the

normalisation factors have been applied.

  * `geometry`: The geometry of the block.
  * `minval`: The minimum coordinate values in each direction.
  * `maxval`: The maximum coordinate values in each direction.

The geometry of the block can take the following values

  * `Null`: Unspecified geometry. This is an error.
  * `Cartesian`: Cartesian geometry.
  * `Cylindrical`: Cylindrical geometry.
  * `Spherical`: Spherical geometry.

The last item in the header is `dims`, is the number of grid points in each dimension.

The data written is the locations of node points for the mesh in each of the simulation dimensions. Therefore for a 3d simulation of resolution $(nx; ny; nz)$, the data will consist of a 1d array of X positions with $(nx + 1)$ elements followed by a 1d array of Y positions with $(ny + 1)$ elements and finally a 1d array of Z positions with $(nz + 1)$ elements. Here the resolution specifies the number of simulation cells and therefore the nodal values have one extra element. In a 1d or 2d simulation, you would write only the X or X and Y arrays respectively.
