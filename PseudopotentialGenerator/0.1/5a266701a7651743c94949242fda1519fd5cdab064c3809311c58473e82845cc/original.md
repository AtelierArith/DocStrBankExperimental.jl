```
derivative(f, mesh, idx)
```

Compute the derivative of the function `f` at the point `idx` using the mesh `mesh`. By fit the polynomial to the function values at the points `idx-5:idx+5` and compute the derivative at the point `idx`.

Can approximate the derivative to ~ 1e-8.
