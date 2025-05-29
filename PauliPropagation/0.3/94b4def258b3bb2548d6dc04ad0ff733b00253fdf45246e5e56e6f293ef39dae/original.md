```
rectangletopology(nx::Integer, ny::Integer; periodic=false)
```

Create a 2D topology on a grid of `nx` by `ny` qubits. The order is none in particular and may need to be adapted for specific purposes. If `periodic` is set to `true`, the grid is connected periodically in both directions.
