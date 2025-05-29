```
setup_vertical_well(g, K, i, j; heel = 1, toe = grid_dims_ijk(g)[3], kwarg...)
```

Set up a vertical well for given grid `g` and permeability `K` at logical indices `i, j` perforating all cells starting at k-logical index `heel` to `toe`.
