```
create_geometry(setup; recreate = true)
```

Create cells, surfaces and finite element mesh. If `recreate = false`, previous geometry will be reused.

This function does the following:

  * Check geometry setup consistency
  * Create or load cell configuration
  * Create or load surface triangulation
  * Call TetGen
  * Deform domain
  * Split mesh into compartments

For custom geometries with more than one compartment, call `split_mesh` directly instead. This requires facet and element labels.
