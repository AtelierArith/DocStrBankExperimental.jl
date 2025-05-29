```
inverse_laplacian!(w::GridData,sys::ILMSystem)
```

Compute the in-place inverse Laplacian of grid data `w`, and multiply the result by unity or by the grid cell size, depending on whether `sys` has `IndexScaling` or `GridScaling`, respectively.
