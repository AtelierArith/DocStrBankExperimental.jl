```
DiskCell
```

A simple two-dimensional growing dumbbell model.

# Extended help

## List of fields

  * `id`, `centerpos`, `params`: InPartS standard fields
  * `nodeseparation`: length of the cell backbone measured between the centres of the circular caps
  * `φ`: angle of the cell backbone w.r.t. the x-Axis
  * `growthprog`: current growth phase of the cell
  * `grothrate`: rate of change of `growthprog`
  * `attached`: if set to true, evolution of every degree of freedom (except for `growthprog`) is stopped. *Currently unused*.
  * `P`, N: node positions
  * `fP`, `fN`: node force accumulators
