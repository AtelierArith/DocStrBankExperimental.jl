```
grid_size(lrs::LatticeReactionSystem)
```

Returns the size of `lrs`'s lattice (only if it is a cartesian or masked grid lattice). E.g. for a lattice `CartesianGrid(4,6)`, `(4,6)` is returned.
