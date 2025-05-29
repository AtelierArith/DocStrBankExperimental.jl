```
OceanCurvilinearGrid
```

Ocean curvilinear grid. The grid is curvilinear if it can be accessed using Cartesian Indices. I.e., it maps to a rectilinear grid. This type of grid typically cannot be inferred from only `lat`, `lon`, `depth`, `δlat`, `δlon`, and `δdepth` vectors. Instead, the full 3-dimensional arrays `lat_3D`, `lon_3D`, `D`epth*3D`,`δx*3D`,`δy*3D`, and`δz*3D` are required. For exaample, the displaced-pole grid of the POP model is curcvilinear.
