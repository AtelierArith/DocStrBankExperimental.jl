```
inverse_laplacian!(w::GridData,cache::BasicILMCache)
```

Compute the in-place inverse Laplacian of grid data `w`, and multiply the result by unity or by the grid cell size, depending on whether `cache` has `IndexScaling` or `GridScaling`, respectively.
