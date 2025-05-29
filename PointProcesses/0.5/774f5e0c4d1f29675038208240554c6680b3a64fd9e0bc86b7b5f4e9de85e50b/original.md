```
AbstractPoissonProcess{M} <: AbstractPointProcess{M}
```

Common interface for all temporal Poisson processes, that is, temporal point processes for which the intensity is not a function of past history.

Implements some fallbacks for the `AbstractPointProcess` interface which accept fewer arguments.
