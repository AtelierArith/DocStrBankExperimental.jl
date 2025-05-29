```
DiskCell3D
```

A three-dimensional version of [`DiskCell`](@ref).

# Extended help

## List of fields

  * `id`, `centerpos`, `params`: InPartS standard fields
  * `nodeseparation`: length of the cell backbone measured between the centres of the circular caps
  * `orientation`: normalized backbone vector of cell
  * `growthprog`: current growth phase of the cell
  * `grothrate`: rate of change of `growthprog`
  * `attached`: if set to true, evolution of every degree of freedom (except for `growthprog`) is stopped. *Currently unused*.
  * `P`, N: node positions
  * `fP`, `fN`: node force accumulators
