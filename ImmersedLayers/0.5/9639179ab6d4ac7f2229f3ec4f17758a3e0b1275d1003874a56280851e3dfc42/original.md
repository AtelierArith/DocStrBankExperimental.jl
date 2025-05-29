```
complementary_mask(w::GridData,surface::Body,grid::PhysicalGrid)
```

Create grid data that consist of 0s inside of surface `surface` (i.e., on a side opposite the normal vectors) and 1s outside. The grid data are the same type as `w`.
