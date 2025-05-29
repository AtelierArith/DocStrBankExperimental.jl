```
FiniteDifferenceGrid(topology::Topologies.IntervalTopology)
FiniteDifferenceGrid(device::ClimaComms.AbstractDevice, mesh::Meshes.IntervalMesh)
```

Construct a `FiniteDifferenceGrid` from an `IntervalTopology` (or an `IntervalMesh`).

This is an object which contains all the necessary geometric information.

To avoid unnecessary duplication, we memoize the construction of the grid.
