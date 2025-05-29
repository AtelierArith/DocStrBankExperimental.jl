```
CylindricalTubeMesh(;dz=1e-9, R=20e-9, nz=1, nr=10, pbc="open")
```

Create a cylindrical tube mesh along the +z direction. 

The spins are located on the cylindrical tube uniformly, and are indexed as follows:

```julia
  id = index(i, 1, k, nr, 1, nz)
```

which means that the spins are labelled in a ring firstly, then `nz` is the number of rings.   The coordinates of the spins at each ring are given as `(R cos(2*pi*(i-1)/nr), R sin(2*pi*(nr-1)/nr))`.

The nearest neighbours are indexed as follows:

|  1      2        3       4            |left   right    bottom   top |
