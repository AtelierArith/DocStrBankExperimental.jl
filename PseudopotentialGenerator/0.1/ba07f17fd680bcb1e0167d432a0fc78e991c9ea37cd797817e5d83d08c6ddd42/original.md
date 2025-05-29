```
Mesh
```

A mesh object that stores the radial grid points and their derivatives. To create a mesh object, use the constructor `Mesh(rmin, rmax, a, N)`.

The radial grid points are generated using the formula:

```
r[i] = rmin + alpha * (exp(beta * (i - 1)) - 1)

alpha = (rmax - rmin) / (exp(beta * N) - 1) 

beta = log(a) / (N - 1).
```

The actual number of points in the mesh is N+1.
