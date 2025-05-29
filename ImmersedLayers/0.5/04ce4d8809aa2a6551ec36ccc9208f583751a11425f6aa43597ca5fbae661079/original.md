```
laplacian!(w::GridData,s::GridData,sys::ILMSystem)
```

Compute the Laplacian of grid data `s`, and divide the result by unity or by the grid cell size, depending on whether `sys` has `IndexScaling` or `GridScaling`, respectively, and return the result as `w`.
