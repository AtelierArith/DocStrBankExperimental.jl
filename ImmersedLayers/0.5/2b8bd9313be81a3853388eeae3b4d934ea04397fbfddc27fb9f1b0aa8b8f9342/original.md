```
laplacian!(w::GridData,s::GridData,cache::BasicILMCache)
```

Compute the Laplacian of grid data `s`, and divide the result by unity or by the grid cell size, depending on whether `cache` has `IndexScaling` or `GridScaling`, respectively, and return the result as `w`.
