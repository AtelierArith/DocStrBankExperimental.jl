```
find_dv!(grid::VoronoiGrid, dt::Float64, alpha::Float64 = 1.0)
```

Determine `dv`, the repair velocity. This is the first step of mesh relaxation procedure and is needed to maintain sufficiently high mesh quality. The repair velocity is chosen to be proportional to Frobenius norm of velocity deformation tensor `D` and inversely proportional to the mesh quality squared. There is also multiplicative dimensionless parameter `alpha` with default value `alpha = 1`. Higher `alpha` causes the Voronoi cells to be rounder (= better) but also less genuinly Lagrangian.
