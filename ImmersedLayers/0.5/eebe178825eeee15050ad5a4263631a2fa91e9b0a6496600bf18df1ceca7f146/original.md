```
inverse_laplacian!(sol::GridData,rhs::GridData,cache::BasicILMCache)
```

Compute the iinverse Laplacian of grid data `rhs`, multiply the result by unity or by the grid cell size, depending on whether `cache` has `IndexScaling` or `GridScaling`, respectively, and return the result as `sol`.
