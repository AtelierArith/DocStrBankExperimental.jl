```
rasterizeDEM(dem, h; k=10, p=2, trimbounds=[0.0 0.0], dembounds=[0.0, 0.0])
```

## Description:

Rasterize the DEM file to generate particles. `dem` is a coordinates Array with three  columns `(x, y, z)`. `h` is the space of the cloud points in `x` and `y` directions,  normally it is equal to the grid size in the MPM simulation. `k` is the number of nearest  neighbors (10 by default), `p` is the power parameter (2 by default), `trimbounds` is the  boundary of the particles, `dembounds` is the boundary of the DEM.
