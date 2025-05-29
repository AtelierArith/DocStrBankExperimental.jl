```
PointVariableBlockHeader{T,N}
```

The `PointVariableBlockHeader` is used to describe a variable which is located relative to the points given in a mesh block.

The block header contains the `base_header` (a `BlockHeader`) and the following metadata

  * `mult`: The normalisation factor applied to the variable data.
  * `units`: The units for this variable after the normalisation factor has

been applied.

  * `mesh_id`: The name(`id`) of the mesh relative to which this block's data is defined.
  * `np`: The number of points.

Similarly to the grid based variable, the data written contains the values of the given variable at each point on the mesh. Since each the location of each point in space is known fully, there is no need for a stagger variable. The data is in the form of a 1d array with `np` elements.
