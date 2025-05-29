```
TriangularMesh(; dx=1e-9, nx=1, ny=1, nz=1, pbc="open")
```

Create a triangular mesh. The index of the nearest neighbours and the next-nearest  neighbours are given as follows:

| nearest index |   location   | next-nearest index |   location   |
|:-------------:|:------------:|:------------------:|:------------:|
|       1       |    right     |         1          |  top-right   |
|       2       |  top-right   |         2          |     top      |
|       3       |   top-left   |         3          |   top-left   |
|       4       |     left     |         4          | bottom-left  |
|       5       | bottom-left  |         5          |    bottom    |
|       6       | bottom-right |         6          | bottom-right |
|       7       |    above     |                    |              |
|       8       |    below     |                    |              |
