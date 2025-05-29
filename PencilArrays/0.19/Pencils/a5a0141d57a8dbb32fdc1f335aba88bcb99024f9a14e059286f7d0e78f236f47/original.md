```
range_remote(p::Pencil, coords, [order = LogicalOrder()])
range_remote(p::Pencil, n::Integer, [order = LogicalOrder()])
```

Get data range held by a given MPI process.

In the first variant, `coords` are the coordinates of the MPI process in the Cartesian topology. They can be specified as a tuple `(i, j, ...)` or as a `CartesianIndex`.

In the second variant, `n` is the linear index of a given process in the topology.
