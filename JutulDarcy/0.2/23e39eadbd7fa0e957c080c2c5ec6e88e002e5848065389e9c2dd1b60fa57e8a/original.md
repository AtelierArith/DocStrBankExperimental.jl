```
setup_well(D::DataDomain, reservoir_cells; skin = 0.0, Kh = nothing, radius = 0.1, dir = :z, name = :Well)
w = setup_well(D, 1, name = :MyWell)         # Cell 1 in the grid
w = setup_well(D, (2, 5, 1), name = :MyWell) # Position (2, 5, 1) in logically structured mesh
w2 = setup_well(D, [1, 2, 3], name = :MyOtherWell)
```

Set up a well in `reservoir_cells` with given skin factor and radius. The order of cells matter as it is treated as a trajectory.

The `name` keyword argument can be left defaulted if your model will only have a single well (named `:Well`). It is highly recommended to provide this whenever a well is set up.

`reservoir_cells` can be one of the following: A Vector of cells, a single cell, a Vector of `(I, J, K)` Tuples or a single Tuple of the same type.
