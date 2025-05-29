```
mask!(w::GridData,surface::Body,grid::PhysicalGrid)
```

Mask the data `w` in place by multiplying it by 1s inside of surface `surface` (i.e., on a side opposite the normal vectors) and 0s outside.
