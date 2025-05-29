```
shaperadius(unitcell, shape, sites)
shaperadius(lat, shape[, sites])
```

Calculate the radius of a shape such that it contains appriximately `sites` sites.

## Arguments

  * `unitcell`: The `UnitCell` of the lattice. Might also be a lattice type.
  * `lat`: The lattice. It is considered that the lattice was constructed in the same shape.
  * `shape`: The shape to calculate the radius for.
  * `sites`: The number of sites the shape should contain.
