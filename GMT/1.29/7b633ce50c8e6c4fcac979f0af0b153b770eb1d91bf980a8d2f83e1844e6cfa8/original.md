```
D = grid2tri(G, G2=nothing; bottom=false, downsample=0, isbase=false, ratio=0.01,
             thickness=0.0, wall_only=false, top_only=false, geog=false)
```

Triangulate the surface defined by the grid `G`, and optionally the bottom surface `G2`.

Other than the triangulation, this function computes also a vertical wall between `G` and `G2`, or between `G` and constant level or a constant thickness. Optionally, computes only the vertical wall or the full closed bodie (that is, including the bottom surface).

The output of this function can be used in $plot3d$ to create 3D views of volume layer.

NOTE: The `G` grid should have a *out-skirt* of NaNs, otherwise just use $grdview$ with the $N$ option.

### Args

  * `G`: A GMTgrid object or a grid file name representing the surface to be triangulated.
  * `G2`: An optional second grid (or file name) representing the bottom surface of the layer. Using this option makes the `thickness` option be ignored.

### Kwargs

  * `bottom`: If true, fully close the body with the bottom surface. By default we don't do this because that surface is often not visible whem elevation view angle is positive. But we may want this if later we want to save this mesh in STL for importing in a 3D viewer software.
  * `downsample`: If the grid is of too high resolution, files here get big and operations slow down with this and later figures may not benefit much. In those cases it is a good idea to downsample the grid. The  `downsample` option accepts an integer reduction factor. `downsample=2` will shrink the grid by a factor two in each dimention, `downsample=3` will shrink it by a factor three etc.
  * `isbase`: If true, we interpret `thickness` option as meaning a contant level value. That is, the vertical wall is computed from the sides of `G` and a constant level provided via the `thickness` option.
  * `ratio`: A slightly tricky parameter that determines how close the computed concave hull is to the true concave hull. A value smaller to 0.005 seems to do it but we normally don't want that close because the vertical wall obtained from this will be too jagged. The default value of 0.01 seems to work well to get a smoother concave hull but one that still fits the objective of getting a nice vertical wall. May need tweaking for specific cases.
  * `thickness`: A scalar representing the layer thickness in the same units as those of the input grid. NOTE: this option is ignored when two grids are passed in input.
  * `wall_only`: If true, only the vertical wall  between `G` and `G2`, or `G` + `thickness` is computed and returned.
  * `top_only`: If true, only the triangulation of `G`is returned.
  * `geog`: If the `G` grid has no referencing information but you know that it is in geographical coordinates set `geog=true`. This information will be added to the triangulation output and is usefull for plotting purposes.

### Returns

A vector of GMTdataset with the triangulated surface and vertical wall, or just the wall or the full closed body.
