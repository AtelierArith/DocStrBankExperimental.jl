```
SimulatorLikelihood(::Type{distType}, obs, data, prior, name=nameof(obs)) where {distType}
```

Creates a `SimulatorLikelihood` with the given distribution type, observable, data source, and prior distribtuion. A custom identifier may also be specified via the `name` argument; by default, the name of the observable is used.
