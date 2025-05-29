```
RodCell
```

A simple two-dimensional growing Spherocylinder (discorectangle?).

Refer to [J. Isensee et al., J. R. Soc. Interface. 19, 20220512 (2022)](https://doi.org/10.1098/rsif.2022.0512) for a description of the model.

# Extended help

## List of fields

  * `id`, `centerpos`, `params`: InPartS standard fields
  * `nodeseparation`: length of the cell backbone measuerd between the centres of the circular caps
  * `φ`: angle of the cell backbone w.r.t. the x-Axis
  * `growthprog`: current growth phase of the cell
  * `grothrate`: rate of change of `growthprog`
  * `attached`: if set to true, evolution of every degree of freedom (except for `growthprog`) is stopped. *Currently unused*.
  * `backbone`: internal representation of the backbone as a `LineSegment2D`
  * `fP`, `fN`: node force accumulators
