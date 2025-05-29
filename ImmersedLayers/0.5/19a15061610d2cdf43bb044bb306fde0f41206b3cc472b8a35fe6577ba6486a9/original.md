```
mask(w::GridData,surface::Body,grid::PhysicalGrid)
```

Create grid data that consist of 1s inside of surface `surface` (i.e., on a side opposite the normal vectors) and 0s outside. The grid data are the same type as `w`.
