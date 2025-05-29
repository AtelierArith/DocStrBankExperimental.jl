```
ThreeDGrid( dimx, nx, dimy, ny, dimz, nz)
```

Generate a cartesians mesh on cube `dimx` x `dimy` x `dimz` with `nx` x `ny` x `nz` points

  * `nx` : indices are in [1:nx]
  * `ny` : indices are in [1:ny]
  * `nz` : indices are in [1:nz]
  * `dimx = xmax - xmin`
  * `dimy = ymax - ymin`
  * `dimz = zmax - zmin`
  * `x, y, z` : node positions
  * `dx, dy, dz` : step size
