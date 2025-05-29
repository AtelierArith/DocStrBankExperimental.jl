```
SystemState(Tv, system; data=system.physics.data, matrixtype=system.matrixtype)
```

Create state information for finite volume system.

Arguments:

  * `Tv`: value type of unknowns, matrix
  * `system`: Finite volume system

Keyword arguments:

  * `data`: User data. Default: `data(system)`
  * `matrixtype`. Default: `system.matrixtype`
