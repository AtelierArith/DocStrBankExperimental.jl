```
InterpolationMatrix(cache::BasicILMCache,src::GridData,trg::PointData)
```

Create a interpolation matrix for regularizing grid data of type `src` to point data of type `trg`. (Both `src` and `trg` must be appropriately sized for the grid and points in `cache`.)
