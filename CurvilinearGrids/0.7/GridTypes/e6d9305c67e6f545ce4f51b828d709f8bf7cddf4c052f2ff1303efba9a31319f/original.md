```
coord(mesh, index::CartesianIndex)
```

Get the position/coordinate at a given index. **NOTE:** these indices are consistent with halo cells included. This means that if your grid has 2 halo cells, the position of the first non-halo vertex is index at coord(mesh, 3). The `CurvilinearGrid` only keeps track of the number of halo cells for each dimension, whereas the grid functions have no knowledge halos. Therefore, the `coord` function applies a shift to the index for you.
