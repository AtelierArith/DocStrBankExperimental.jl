```
PlainVariableBlockHeader{T,N}
```

The `PlainVariableBlockHeader` is used to describe a variable which is located relative to the points given in a mesh block.

The block header contains the `base_header` (a `BlockHeader`) and the following metadata

  * `mult`: The normalisation factor applied to the variable data.
  * `units`: The units for this variable after the normalisation factor has

been applied.

  * `mesh_id`: The name(`id`) of the mesh relative to which this block's data is defined.
  * `dims`: The number of grid points in each dimension.
  * `stagger`: The location of the variable relative to its associated mesh.

The mesh associated with a variable is always node-centred, i.e. the values written as mesh data specify the nodal values of a grid. Variables may be defined at points which are offset from this grid due to grid staggering in the code. The `stagger` entry specifies where the variable is defined relative to the mesh. Since we have already defined the number of points that the associated mesh contains, this determines how many points are required to display the variable.

The `stagger` entry can take one of the following values

  * `CellCentre`: Cell centred. At the midpoint between nodes. Implies an

$(nx; ny; nz)$ grid.

  * `FaceX`: Face centred in X. Located at the midpoint between nodes on

the Y-Z plane. Implies an $(nx + 1; ny; nz)$ grid.

  * `FaceY`: Face centred in Y. Located at the midpoint between nodes on

the X-Z plane. Implies an $(nx; ny + 1; nz)$ grid.

  * `FaceZ`: Face centred in Z. Located at the midpoint between nodes on

the X-Y plane. Implies an $(nx; ny; nz + 1)$ grid.

  * `EdgeX`: Edge centred along X. Located at the midpoint between nodes

along the X-axis. Implies an $(nx; ny + 1; nz + 1)$ grid.

  * `EdgeY`: Edge centred along Y. Located at the midpoint between nodes

along the Y-axis. Implies an $(nx + 1; ny; nz + 1)$ grid.

  * `EdgeZ`: Edge centred along Z. Located at the midpoint between nodes

along the Z-axis. Implies an $(nx + 1; ny + 1; nz)$ grid.

  * `Vertex`: Node centred. At the same place as the mesh. Implies an ``(nx+

1; ny + 1; nz + 1)`` grid.

For a grid based variable, the data written contains the values of the given variable at each point on the mesh. This is in the form of a 1d, 2d or 3d array depending on the dimensions of the simulation. The size of the array depends on the size of the associated mesh and the grid staggering as indicated above. It corresponds to the values written into the `dims` array written for this block.
