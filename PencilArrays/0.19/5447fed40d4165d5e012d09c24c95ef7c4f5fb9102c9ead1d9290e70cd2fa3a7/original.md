```
range_remote(x::PencilArray, coords, [order = LogicalOrder()])
range_remote(x::PencilArrayCollection, coords, [order = LogicalOrder()])
```

Get data range held by the `PencilArray` in a given MPI process.

The location of the MPI process in the topology is determined by the `coords` argument, which can be given as a linear or Cartesian index.

See [`range_remote(::Pencil, ...)`](@ref range_remote(::Pencil, ::Integer, ::LogicalOrder)) variant for details.
